set(COMPONENT_ADD_INCLUDEDIRS "./wifi_config"
                              "./ota_esp"
                              "./samples"
                              "./factory_restore"
                              ".")

# Edit following two lines to set component requirements (see docs)
set(COMPONENT_REQUIRES)
set(COMPONENT_PRIV_REQUIRES )

set(COMPONENT_SRCS ./ota_esp/qcloud_iot_ota_esp.c ./main.c ./board_ops.c ./led_strip_rmt_ws2812.c ./factory_restore/factory_restore.c)


#ifdef CONFIG_SMART_LIGHT_ENABLED
file(GLOB src_sample ${CMAKE_CURRENT_SOURCE_DIR}/samples/data_template_light/*.c)
list(APPEND COMPONENT_SRCS ${src_sample})
#endif

#ifdef CONFIG_WIFI_CONFIG_ENABLED
file(GLOB src_wifi ${CMAKE_CURRENT_SOURCE_DIR}/wifi_config/*.c)
list(APPEND COMPONENT_SRCS ${src_wifi})
#endif

register_component()
