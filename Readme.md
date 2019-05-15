## What is Prometheus

  Prometheus is a 21st century monitoring solution. Which architected as asynchronous server-client scrape system.
  
## Installing Prometheus

  Following instruction will setup a single node Prometheus cluster in docker-swarm, with node-exporter (to export system metrics)
  
  1. Clone [monitoring repo](https://github.com/rjshrjndrn/monitoring)
  2. `cd monitoring/ansible/`
  3. fill inventory/hosts
  4. Installing  Docker
      1. ansible-playbook -i inventory setup-dockerswarm.yml
  5. Setup Prometheus and grafana
      1. ansible-playbook -i inventory monitoring.yml
  6. Setting up grafana Data source
      1. goto http://{prometheus-machine-ip}:3000/ use user: admin and passowrd: defined in grafana_admin_password variable inthe [monitoring yml](monitoring.yml)
      2. click on settings -> Data sources -> select Prometheus
      3. url -> http://{prometheus-machine-ip}:9090/prometheus -> save and test. This will configure data source
  7. first Dashboard
      1. click on '+' sign -> import
      2. put `1860` in `Grafana.com Dashboard` field and load
      3. select datasource and import
