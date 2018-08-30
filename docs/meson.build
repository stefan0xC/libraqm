docs_dir = include_directories('.')

config = configuration_data()
config.set('VERSION', version)
version_xml = configure_file(input : 'version.xml.in',
                             output : 'version.xml',
                             configuration: config)
gnome.gtkdoc('raqm',
           main_xml: 'raqm-docs.xml',
            src_dir: [ join_paths(meson.source_root(), 'src') ],
            scan_args: [
                    '--rebuild-sections',
                    ],
          mkdb_args: [
                '--xml-mode',
                '--output-format=xml',
                ],
        install_dir: 'raqm',
            install: true)

