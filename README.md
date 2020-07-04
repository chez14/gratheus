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

- Change the settings user on the `docker-compose.yml` file.

- chown && chmod, if you need.
    ```shell
    $ chown -R 1001:1001 .data
    ```
- Then you can `docker-compose up` the nuclear faciltiy.

- After that, you can login to the grafana:
  - URL: http://localhost
  - Username: `monitoring` (UNLESS you changed the setting on `docker-compose.yml`!)
  - Password: `securePassword` (UNLESS you changed the setting on `docker-compose.yml`!)
