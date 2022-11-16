# 08-ansible-04
Установка ролей:
ansible-galaxy install -r requirements.yml -p roles/ --force

Запуск плэйбука
ansible-playbook playbook.yml

Результат:

ansible@ansible:~/ansible$ ansible-playbook playbook.yml

PLAY [Install Clickhouse] *************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Include OS Family Specific Variables] ******************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
included: /home/ansible/ansible/roles/clickhouse/tasks/precheck.yml for clickhouse_01

TASK [clickhouse : Requirements check | Checking sse4_2 support] **********************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Requirements check | Not supported distribution && release] ********************************************************************************************
skipping: [clickhouse_01]

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
included: /home/ansible/ansible/roles/clickhouse/tasks/params.yml for clickhouse_01

TASK [clickhouse : Set clickhouse_service_enable] *************************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Set clickhouse_service_ensure] *************************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
included: /home/ansible/ansible/roles/clickhouse/tasks/install/apt.yml for clickhouse_01

TASK [clickhouse : Install by APT | Apt-key add repo key] *****************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Install by APT | Remove old repo] **********************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Install by APT | Repo installation] ********************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Install by APT | Package installation] *****************************************************************************************************************
skipping: [clickhouse_01]

TASK [clickhouse : Install by APT | Package installation] *****************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Hold specified version during APT upgrade | Package installation] **************************************************************************************
ok: [clickhouse_01] => (item=clickhouse-client)
ok: [clickhouse_01] => (item=clickhouse-server)
ok: [clickhouse_01] => (item=clickhouse-common-static)

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
included: /home/ansible/ansible/roles/clickhouse/tasks/configure/sys.yml for clickhouse_01

TASK [clickhouse : Check clickhouse config, data and logs] ****************************************************************************************************************
ok: [clickhouse_01] => (item=/var/log/clickhouse-server)
ok: [clickhouse_01] => (item=/etc/clickhouse-server)
ok: [clickhouse_01] => (item=/var/lib/clickhouse/tmp/)
ok: [clickhouse_01] => (item=/var/lib/clickhouse/)

TASK [clickhouse : Config | Create config.d folder] ***********************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Config | Create users.d folder] ************************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Config | Generate system config] ***********************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Config | Generate users config] ************************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Config | Generate remote_servers config] ***************************************************************************************************************
skipping: [clickhouse_01]

TASK [clickhouse : Config | Generate macros config] ***********************************************************************************************************************
skipping: [clickhouse_01]

TASK [clickhouse : Config | Generate zookeeper servers config] ************************************************************************************************************
skipping: [clickhouse_01]

TASK [clickhouse : Config | Fix interserver_http_port and intersever_https_port collision] ********************************************************************************
skipping: [clickhouse_01]

TASK [clickhouse : Notify Handlers Now] ***********************************************************************************************************************************

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
included: /home/ansible/ansible/roles/clickhouse/tasks/service.yml for clickhouse_01

TASK [clickhouse : Ensure clickhouse-server.service is enabled: True and state: started] **********************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Wait for Clickhouse Server to Become Ready] ************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
included: /home/ansible/ansible/roles/clickhouse/tasks/configure/db.yml for clickhouse_01

TASK [clickhouse : Set ClickHose Connection String] ***********************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Gather list of existing databases] *********************************************************************************************************************
ok: [clickhouse_01]

TASK [clickhouse : Config | Delete database config] ***********************************************************************************************************************

TASK [clickhouse : Config | Create database config] ***********************************************************************************************************************

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
included: /home/ansible/ansible/roles/clickhouse/tasks/configure/dict.yml for clickhouse_01

TASK [clickhouse : Config | Generate dictionary config] *******************************************************************************************************************
skipping: [clickhouse_01]

TASK [clickhouse : include_tasks] *****************************************************************************************************************************************
skipping: [clickhouse_01]

PLAY [Install Vector] *****************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************
ok: [vector_01]

TASK [vector-role : NGINX -> Install Nginx] *******************************************************************************************************************************
ok: [vector_01]

TASK [vector-role : NGINX -> Create general config] ***********************************************************************************************************************
ok: [vector_01]

TASK [vector-role : Vector -> Download deb-distrib] ***********************************************************************************************************************
ok: [vector_01]

TASK [vector-role : Vector -> Install deb-packages] ***********************************************************************************************************************
ok: [vector_01]

PLAY [Install Lighthouse] *************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************
ok: [lighthouse_01]

TASK [lighthouse-role : Lighthouse -> install git] ************************************************************************************************************************
ok: [lighthouse_01]

TASK [lighthouse-role : NGINX -> install Nginx] ***************************************************************************************************************************
ok: [lighthouse_01]

TASK [lighthouse-role : NGINX -> Create general config] *******************************************************************************************************************
ok: [lighthouse_01]

TASK [lighthouse-role : Lighthouse -> github] *****************************************************************************************************************************
ok: [lighthouse_01]

TASK [lighthouse-role : lighthouse -> nginx config] ***********************************************************************************************************************
ok: [lighthouse_01]

PLAY RECAP ****************************************************************************************************************************************************************
clickhouse_01              : ok=26   changed=0    unreachable=0    failed=0    skipped=10   rescued=0    ignored=0
lighthouse_01              : ok=6    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
vector_01                  : ok=5    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
