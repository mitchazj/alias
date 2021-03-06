project('com.github.bartzaalberg.alias', 'vala', 'c')

gnome = import('gnome')
i18n = import('i18n')

add_global_arguments('-DGETTEXT_PACKAGE="@0@"'.format (meson.project_name()), language:'c')

asresources = gnome.compile_resources(
    'as-resources', 'data/icons/icons.gresource.xml',
    source_dir: 'data/icons',
    c_name: 'as'
)

executable(
    meson.project_name(),
    'src/Application.vala',
    'src/MainWindow.vala',
    'src/ListBoxRow.vala',
    'src/ListBox.vala',
    'src/Constants.vala',
    'src/StackManager.vala',
    'src/ListManager.vala',
    'src/ResponseTranslator.vala',
    'src/FileManager.vala',
    'src/CommandManager.vala',
    'src/Alias.vala',
    'src/Dialogs/Alert.vala',
    'src/Dialogs/DeleteConfirm.vala',
    'src/Views/ListView.vala',
    'src/Views/NotFoundView.vala',
    'src/Views/WelcomeView.vala',
    'src/Views/EditView.vala',
    'src/Views/CreateView.vala',
    'src/Components/FormComponent.vala',
    'src/Components/FormLabel.vala',
    'src/Components/FormEntry.vala',
    'src/Components/HeaderBar.vala',
    'src/Components/HeaderLabel.vala',
    asresources,
    dependencies: [
        dependency('gtk+-3.0'),
        dependency('granite')
    ],
    install: true
)

subdir('data')
subdir('po')

install_data(
    join_paths('data', meson.project_name() + '.desktop'),
    install_dir: join_paths(get_option('datadir'), 'applications')
)

install_data(
    join_paths('data', meson.project_name() + '.appdata.xml'),
    install_dir: join_paths(get_option('datadir'), 'metainfo')
)

python3 = import('python3').find_python()
run_command(python3, '-c', 'import shutil; shutil.copy("hooks/pre-commit.hook", ".git/hooks/pre-commit")')
