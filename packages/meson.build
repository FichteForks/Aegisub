c_pkg = configuration_data()
c_pkg.set('AEGISUB_COMMAND', 'aegisub')

if host_machine.system() == 'windows'
elif host_machine.system() == 'darwin'
else
    desktop_template = configure_file(input : 'desktop/aegisub.desktop.template.in',
                                      output : 'aegisub.desktop.template',
                                      configuration : c_pkg)

    intltool_merge = find_program('intltool-merge')
    desktop = custom_target('aegisub.desktop',
                            input : desktop_template,
                            output : 'aegisub.desktop',
                            command : [intltool_merge, '--desktop-style', '--quiet', '../po', '@INPUT@', '@OUTPUT@'],
                            install : true,
                            install_dir : join_paths(get_option('datadir'), 'applications'))
endif

foreach s : ['16x16.png', '22x22.png', '24x24.png', '32x32.png',
             '48x48.png', '64x64.png', 'scalable.svg']
    dir = s.split('.')[0]
    ext = s.split('.')[1]
    install_data(join_paths('desktop', dir, 'aegisub.' + ext),
                 install_dir : join_paths(get_option('datadir'), 'icons', 'hicolor', dir, 'apps'))
endforeach
