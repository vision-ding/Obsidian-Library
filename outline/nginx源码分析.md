1.module_type是NGX_CORE_MODULE的模块有哪些：
ngx_core_module
ngx_errlog_module
ngx_events_module
ngx_http_module

2.module_type是NGX_CONF_MODULE的模块有哪些：
ngx_conf_module

3.module_type是NGX_EVENT_MODULE的模块有哪些：
ngx_event_core_module
ngx_epoll_module

3.module_type是NGX_HTTP_MODULE的模块有哪些：
ngx_http_core_module
ngx_http_headers_filter_module
ngx_http_upstream_module

nginx在什么时候初始化listening的回调函数:
当http_module解析配置时，会调用ngx_http_block --> ngx_http_optimize_servers --> ngx_http_init_listening 
--> ngx_http_add_listening --> ngx_http_init_connection(listening的回调函数)

nginx在什么时候启动对端口的监听：
ngx_init_cycle --> ngx_open_listening_sockets

nginx在什么时候将监听事件添加到epoll:
ngx_start_worker_processes --> ngx_spawn_process --> ngx_worker_process_cycle --> ngx_worker_process_init --> ngx_event_process_init

nginx从哪个方法开始处理请求
ngx_http_handler

处理http请求的11个阶段
NGX_HTTP_POST_READ_PHASE				ngx_http_core_generic_phase					ngx_http_core_rewrite_phase/ngx_http_core_find_config_phase
NGX_HTTP_SERVER_REWRITE_PHASE			ngx_http_core_rewrite_phase					ngx_http_core_find_config_phase
!NGX_HTTP_FIND_CONFIG_PHASE				ngx_http_core_find_config_phase				nil
NGX_HTTP_REWRITE_PHASE					ngx_http_core_rewrite_phase					ngx_http_core_post_rewrite_phase/ngx_http_core_generic_phase
!NGX_HTTP_POST_REWRITE_PHASE			ngx_http_core_post_rewrite_phase			ngx_http_core_find_config_phase
NGX_HTTP_PREACCESS_PHASE				ngx_http_core_generic_phase					ngx_http_core_access_phase
NGX_HTTP_ACCESS_PHASE					ngx_http_core_access_phase					ngx_http_core_post_access_phase/ngx_http_core_generic_phase
!NGX_HTTP_POST_ACCESS_PHASE				ngx_http_core_post_access_phase				ngx_http_core_generic_phase
!NGX_HTTP_TRY_FILES_PHASE				ngx_http_core_generic_phase					ngx_http_core_content_phase
NGX_HTTP_CONTENT_PHASE					ngx_http_core_content_phase					nil
NGX_HTTP_LOG_PHASE						nil



编译包含的模块：
    &ngx_core_module,
    &ngx_errlog_module,
    &ngx_conf_module,
    &ngx_events_module,
    &ngx_event_core_module,
    &ngx_epoll_module,
    &ngx_openssl_module,
    &ngx_regex_module,
    &ngx_http_module,
    &ngx_http_core_module,
    &ngx_http_log_module,
    &ngx_http_upstream_module,
    &ngx_http_static_module,
    &ngx_http_gzip_static_module,
    &ngx_http_autoindex_module,
    &ngx_http_index_module,
    &ngx_http_auth_basic_module,
    &ngx_http_access_module,
    &ngx_http_limit_conn_module,
    &ngx_http_limit_req_module,
    &ngx_http_realip_module,
    &ngx_http_geo_module,
    &ngx_http_map_module,
    &ngx_http_split_clients_module,
    &ngx_http_referer_module,
    &ngx_http_rewrite_module,
    &ngx_http_ssl_module,
    &ngx_http_proxy_module,
    &ngx_http_fastcgi_module,
    &ngx_http_uwsgi_module,
    &ngx_http_scgi_module,
    &ngx_http_memcached_module,
    &ngx_http_empty_gif_module,
    &ngx_http_browser_module,
    &ngx_http_upstream_hash_module,
    &ngx_http_upstream_ip_hash_module,
    &ngx_http_upstream_least_conn_module,
    &ngx_http_upstream_keepalive_module,
    &ngx_http_stub_status_module,
    &ngx_http_write_filter_module,
    &ngx_http_header_filter_module,
    &ngx_http_chunked_filter_module,
    &ngx_http_range_header_filter_module,
    &ngx_http_gzip_filter_module,
    &ngx_http_postpone_filter_module,
	&ngx_http_ssi_filter_module,
    &ngx_http_charset_filter_module,
    &ngx_http_userid_filter_module,
    &ngx_http_headers_filter_module,
    &ngx_http_copy_filter_module,
    &ngx_http_range_body_filter_module,
    &ngx_http_not_modified_filter_module,



