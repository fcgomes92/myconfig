#### Docker aliases

```bash
alias dk-compose-adpf='cd ~/dev/docker-stack/; docker-compose up -d'
alias dk-stop-adpf='cd /home/adianta/dev/docker-stack/; docker-compose stop'
alias dk-adpf-celery='docker exec -it celery bash -c "supervisorctl stop all && su - python"'
alias dk-cnab='docker exec -it cnab-celery bash -c "supervisorctl stop all && su - python"'
alias dk-adpf='docker exec -it flask bash -c "supervisorctl stop all && su - python"'
alias dk-admin='docker exec -it backend_admin bash -c "supervisorctl stop all && su - python"'
alias dk-partner='docker exec -it backend_partner bash -c "supervisorctl stop all && su - python"'
alias dk-compose-mtdc='cd /home/adianta/dev/mtdc_docker/; docker-compose up -d'
alias dk-stop-mtdc='cd /home/adianta/dev/mtdc_docker/; docker-compose stop'
alias dk-decision='docker exec -it mtdc_decision bash -c "supervisorctl stop all && su - python"'
alias dk-decision-celery='docker exec -it celery_decision bash -c "supervisorctl stop all && su - python"'
alias dk-ingestion='docker exec -it mtdc_ingestion bash -c "supervisorctl stop all && su - python"'
alias dk-collector='docker exec -it mtdc_collector bash -c "supervisorctl stop all && su - python"'
```
