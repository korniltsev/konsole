add_executable(konsole_globalaccel
    konsole_globalaccel.cpp
)

target_link_libraries(konsole_globalaccel PRIVATE
    KF5::ConfigCore
    KF5::GlobalAccel
    KF5::Service
)


set(konsole_show_menubar_SRCS konsole_show_menubar.cpp)
qt_add_resources(konsole_show_menubar_SRCS ../desktop/konsole.qrc)

add_executable(konsole_show_menubar ${konsole_show_menubar_SRCS})

target_link_libraries(konsole_show_menubar
    KF5::XmlGui
)


install(FILES konsole.upd DESTINATION ${KDE_INSTALL_KCONFUPDATEDIR})
install(PROGRAMS konsole_add_hamburgermenu_to_toolbar.sh DESTINATION ${KDE_INSTALL_KCONFUPDATEDIR})
install(TARGETS konsole_globalaccel konsole_show_menubar DESTINATION ${KDE_INSTALL_LIBDIR}/kconf_update_bin)
