# Home Dashboard Infra

Infra related code for the home dashboard project

### Overview



This project contains code to run the project both locally and on the raspberrypi, the intent is to get the user up 
and running as fast as possible by using docker compose and the latest pre build containers for all the services. 
If you are working on the FE, you'll need to comment out the `home-dashboard-fe` portion of the compose file or the 
`home-dashboard-be` if your working on the backend.

In either case, you will need to fill in the following env vars for `home-dashboard-be` before running `docker-compose up`

```
OCTOPUS_API_KEY: sk_live_x
TFL_API_KEY: x
OCTOPUS_ACCOUNT_NUMBER: x
```

## The intended destination

Eventually, the application will be deployed differently to the way it is now. The intent is to have it deployed to a 
kubernetes system like follows

[Intended architecture](./diagrams/HomeDashboard.drawio.png)



- `docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx`
- `docker run --name my-custom-nginx-container -v ~/home-dashboard-infra/nginx/nginx.conf:/etc/nginx/nginx.conf:ro -v ~/home-dashboard-infra/nginx/conf.d/default.conf:/etc/nginx/conf.d/default.conf -d -p 80:80--add-host=host.docker.internal:host-gateway nginx`
- `docker run --name my-custom-nginx-container -v ~/home-dashboard-infra/nginx/nginx.conf:/etc/nginx/nginx.conf:ro -v ~/home-dashboard-infra/nginx/conf.d/default.conf:/etc/nginx/conf.d/default.conf -v ~/home-dashboard-fe/build:/usr/share/nginx/html/home-dashboard -d -p 80:80 --add-host=host.docker.internal:host-gateway nginx`