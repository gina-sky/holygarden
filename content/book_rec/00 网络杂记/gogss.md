```
    set $is_get_request 0;

    if ($request_method = GET) {

        set $is_get_request 1;

    }

location ~ ^/user/(login|sign_up|forgot_password|reset_password) {

	# 判断请求方法：GET重定向，非GET(POST等)代理
	if ($is_get_request) {
	# GET请求重定向到/gogs路径
	return 301 $scheme://$host/gogss$request_uri$is_args$args;
	}

	# 非GET请求直接代理到后端(保留POST数据)
	proxy_pass http://127.0.0.1:3000;
	proxy_set_header Host $host;
	proxy_set_header X-Real-IP $remote_addr;
	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	proxy_set_header X-Forwarded-Proto $scheme;
	proxy_set_header Content-Type $content_type;
	proxy_set_header Content-Length $content_length;
	# 修复后端重定向
	proxy_redirect https://$host/ https://$host/gogss/;

}

location ~ ^/user/(login|sign_up|forgot_password|reset_password) {

	# 判断请求方法：GET重定向，非GET(POST等)代理
	if ($is_get_request) {
	# GET请求重定向到/gogs路径
	return 301 $scheme://$host/gogss$request_uri$is_args$args;
	}

	# 非GET请求直接代理到后端(保留POST数据)
	proxy_pass http://127.0.0.1:3000;
	proxy_set_header Host $host;
	proxy_set_header X-Real-IP $remote_addr;
	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	proxy_set_header X-Forwarded-Proto $scheme;
	proxy_set_header Content-Type $content_type;
	proxy_set_header Content-Length $content_length;
	# 修复后端重定向
	proxy_redirect https://$host/ https://$host/gogss/;

}


```
