# Monitoring Dashboard
This is a basic template for your daily monitoring things.

In this package:
- Grafana, for beautiful dashboard
- Prometheus, for the exporters

You run this on docker by simple run this sacred script:
```shell
$ docker-compose up
```

## But before that,
You'll have to fine tune the installation before it went to production. Things such as user and presistent
storage stuff that need to be taken care of before spinning up the server is quite.... important.

So in a nushell here's what you need to do:
- Create data folder for storage:
    ```shell
    $ mkdir .data
    ```
- Change the running user on the `docker-compose.yml` file.
  
  Please take a look at this part of the service:
    ```yaml
    services:
        grafana:
            image: grafana/grafana:latest
            links:
            - prometheus
            volumes:
            - ./.data/grafana:/var/lib/grafana
            ports:
            - '80:3000'
            # DON'T FORGET TO UPDATE THIS
            user: "1001:1001" 
    ```
- chmod, if you need.
    ```shell
    $ chmod -R 1001:1001 .data
    ```
- Then you can `docker-compose up` the nuclear faciltiy.

- After that, you can login to the grafana:
  - URL: http://localhost
  - Username: `admin`
  - Password: `admin`

- Adding your Prometheus instance (I'll automate this with [the docs](https://grafana.com/docs/grafana/latest/administration/provisioning/#datasources?utm_source=grafana_ds_list)):
  - Go to http://localhost/datasources
  - Select Prometheus and add the following credential:
    - Url: http://prometheus:9090
  - Click Test & Save
  - Click Back.
  