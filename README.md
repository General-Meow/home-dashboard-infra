# Home Dashboard Infra

Infra related stuff for the home dashboard project

- `docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx`
- `docker run --name my-custom-nginx-container -v ~/home-dashboard-infra/nginx/nginx.conf:/etc/nginx/nginx.conf:ro -v ~/home-dashboard-infra/nginx/conf.d/default.conf:/etc/nginx/conf.d/default.conf -d -p 80:80--add-host=host.docker.internal:host-gateway nginx`
- `docker run --name my-custom-nginx-container -v ~/home-dashboard-infra/nginx/nginx.conf:/etc/nginx/nginx.conf:ro -v ~/home-dashboard-infra/nginx/conf.d/default.conf:/etc/nginx/conf.d/default.conf -v ~/home-dashboard-fe:/usr/share/nginx/html/home-dashboard -d -p 80:80--add-host=host.docker.internal:host-gateway nginx`