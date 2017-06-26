# HPACK-Encode
Encode strings with HPACK to produce a valid Server header for Nginx.

<br/>
The Nginx source contains the Server header "nginx" when using HTTP/2:

    static const u_char nginx[5] = "\x84\xaa\x63\x55\xe7";

It can be seen here: https://trac.nginx.org/nginx/browser/nginx/src/http/v2/ngx_http_v2_filter_module.c#L146

<br/>
To replace this we need to HPACK encode the replacement string. Modify the script and replace `Encrypt All The Things!!!` with your desired Server header. Run the script with `go run encode.go` and it will ouput the required line of code:

    static const u_char nginx[22] = "\x95\xc1\x51\x2c\xf5\x5a\x54\x86\x8a\x14\xdf\x39\x54\xdf\x39\xaa\x99\x1f\xc7\xf1\xfc\x7f";
    
Replace this in the Nginx source and build.
