file(GLOB PY_FILES *.py)

PLUGIN_INSTALL(db_manager db_plugins/postgis ${PY_FILES} ${PYRC_FILES})
PLUGIN_INSTALL(db_manager db_plugins/postgis/icons ${ICON_FILES})

add_subdirectory(plugins)

if(ENABLE_TESTS)
  include(UsePythonTest)
  if (ENABLE_PGTEST)
    ADD_PYTHON_TEST(dbmanager-postgis-connector connector_test.py)
    ADD_PYTHON_TEST(dbmanager-postgis-plugin plugin_test.py)
  endif()
endif()
