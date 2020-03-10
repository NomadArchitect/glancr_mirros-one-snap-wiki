**Overview**

[[_TOC_]]


## Prerequisites

Developing a mirr.OS extension is best done in a local environment where you have full debug access to all system parts. To get things running, you'll need:

- [git](https://git-scm.com)
- Ruby >= 2.6.3; preferably through version managers like [rbenv](https://github.com/rbenv/rbenv) or [asdf](https://asdf-vm.com/#/)
- MySQL >= 5.7 accepting connections on localhost
- Node.js >= 10.15.0
- Recommended: [Vue DevTools](https://github.com/vuejs/vue-devtools) extension for Chrome or Firefox, or the standalone Electron app

## Setting up and running mirr.OS components

Clone these repositories to your local machine and see their README files for setup and running instructions.

- [Backend](https://gitlab.com/glancr/mirros_api)
- [display app](https://gitlab.com/glancr/mirros_display)
- [settings app](https://gitlab.com/glancr/mirros_settings)

## Generating an extension skeleton

To ease the grunt work and help you understand mirr.OS extension conventions, we have Rails generators for both widgets and sources. This is often referred to as “scaffolding”.

Extension names can be any valid name that is not already taken by an existing extension. Valid names consist of latin characters and underscore. It is a Ruby convention to use snake_case for gem names, and mirr.OS extensions are distributed as gems. So please adhere to this naming scheme to avoid naming confusion.

### Scaffolding a widget

Open the folder where you've cloned the backend to on a command line, and run this comman:

```bash
# /some/path/to/mirros_api_repository
bin/rails generate mirros_widget insert_your_widget_machine_name
```

Valid names are lowercase letters, words separated by underscores. See [rubygems.org docs](https://guides.rubygems.org/name-your-gem/) on naming patterns.

After you've run the generator, you can find your widget's files in the `widgets` folder of your mirros_api repository.


## Folders and files of your extension

Take the `public_transport_departures` widget as an example:

```bash
├── Gemfile
├── Gemfile.lock
├── MIT-LICENSE
├── README.md
├── Rakefile
├── app
│   └── assets
│       ├── icons # dummy icon, replace with an SVG
│       │   └── public_transport_departures.svg
│       └── templates # Templates for the UI apps
│           ├── display.vue
│           └── settings.vue
├── bin
│   └── rails
├── config
│   └── routes.rb # custom routing, if required
├── lib
│   ├── public_transport_departures
│   │   ├── engine.rb
│   │   └── version.rb # current version
│   └── public_transport_departures.rb
├── public_transport_departures.gemspec # metadata and dependencies
└── test
    ├── [... test files]

```

### Scaffolding a data source

```bash
bin/rails generate mirros_source my_source_name
```

In contrast to the widget before, the source `sbb` has some different files:

```
├── Gemfile
├── Gemfile.lock
├── MIT-LICENSE
├── README.md
├── Rakefile
├── app
│   ├── assets
│   │   ├── icons
│   │   │   └── sbb.svg
│   │   └── templates
│   │       └── settings.vue # only settings form required
│   └── models
│       └── sbb
│           ├── application_record.rb
│           └── public_transport.rb # Inherits GroupSchemas model
├── bin
│   └── rails
├── config
│   └── routes.rb
├── db
│   └── migrate
├── lib
│   ├── sbb
│   │   ├── engine.rb
│   │   └── version.rb
│   └── sbb.rb
    # Contains Hooks class which implements methods for data refresh
├── sbb.gemspec
└── test
    ├── [... test files]
```

## Getting your extension into the database

mirr.OS needs to know about your newly created extension. The generator adds it to the API Gemfile, and we have some helper tasks to insert it into the development database.

```
bin/rails extension:insert[widget, my_test_widget]
# > Inserted widget my_test_widget into the development database
```

This command reads the metadata from your extension's `gemspec` file and creates a new entry in the development database. It basically “installs” the extension.

## Locating your extension in the UI

If your dev servers are not running yet, check the README's of the API/Settings/Display repositories for instructions. The gist:

```bash
# in mirros_api repository
rails s

# in mirros_settings repository
yarn serve

# in mirros_display repository
yarn serve
```

Now open the mirr.OS Settings app running at http://localhost:8080 (or 8081 if you started the Display app first), then navigate to the “Widgets” or “Sources” tab and see your new extension in action:

![Bildschirmfoto_2019-04-03_um_23.00.57](uploads/076d09a4875209c901ba293eaa010108/Bildschirmfoto_2019-04-03_um_23.00.57.png)

## Updating your extension's metadata

Ok, the title and description of our new extension could be improved …

Open up `<my_test_widget>.gemspec` in your extension's folder and edit the `s.description` with a short sentence in English that explains what your extension does. **Attention: everything beyond 110 characters will be truncated in the UI!**

mirr.OS uses the gemspec specification `metdata` field a bit “creatively” which lets developers add localized metadata and specify how their extension integrates with others. To [keep the gemspec file valid](https://guides.rubygems.org/specification-reference/#metadata), all custom metadata is put in a JSON hash. You don't have to bother with this, just keep in mind that the metadata object has to be a valid Ruby hash.

All fields in the generated gemspec have comments about their possible values. You can delete those comments if you prefer.

```ruby
Gem::Specification.new do |s|
  s.name        = "my_test_widget"
  s.description = "Does awesome things. Batteries included."
  s.license     = "MIT"
  s.metadata    = { 'json' =>
                  {
                    type: 'widgets',
                    title: {
                      enGb: 'My awesome widget',
                      deDe: 'Mein tolles Widget',
                      esEs: 'mi gran widget'
                    },
                    description: {
                      enGb: s.description,
                      deDe: 'Macht großartige Dinge. Batterien enthalten.',
                      esEs: 'Hace cosas increíbles. Baterias incluidas.'
                    },
                    sizes: [
                      {
                        w: 2,
                        h: 2
                       }
                    ],
                    # Add all languages for which your Vue templates are fully translated.
                    languages: [:enGb, :deDe, :esEs],
                    # Add a group if your widget integrates with a specific data type.
                    group: nil,
                    # Prevents installing/updating widgets if the running mirr.OS version is below this.
                    compatibility: '0.9.0'
                  }.to_json
                }
end
```

Once you're happy with the metadata, you need to update the database entry with:

```bash
bin/rails extension:update[widget, my_test_widget]
```
Much better!
![Bildschirmfoto_2019-04-03_um_23.20.43](uploads/12bca806cb19e1bc2c3374e543b8c73d/Bildschirmfoto_2019-04-03_um_23.20.43.png)