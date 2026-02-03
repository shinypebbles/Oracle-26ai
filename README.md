# Oracle-26ai

sudo dnf install -y java-17-openjdk

sudo dnf install -y java-17-openjdk-devel

sudo dnf install -y oracle-database-preinstall-23ai

sudo mkdir -p /home/u01
sudo mkdir -p /u01
sudo mount --bind /home/u01 /u01
echo "/home/u01 /u01 none bind 0 0" | sudo tee -a /etc/fstab
/home/u01 /u01 none bind 0 0

sudo dnf install -y oracle-ai-database-preinstall-26ai

sudo mkdir -p /u01/app/oracle
sudo mkdir -p /u01/app/oraInventory
sudo mkdir -p /u01/app/oracle/stage/autoupgrade
sudo mkdir -p /u01/app/oracle/stage/autoupgrade/logs
sudo mkdir -p /u01/app/oracle/stage/autoupgrade/keystore
sudo mkdir -p /u01/app/oracle/stage/autoupgrade/patches
sudo mkdir -p /u01/app/oracle/product/23.0.0/dbhome_1

sudo chown -R oracle:oinstall /u01/app/oracle
sudo chown -R oracle:oinstall /u01/app/oraInventory

sudo passwd oracle

su - oracle

wget -O /u01/app/oracle/stage/autoupgrade/autoupgrade.jar \
  https://download.oracle.com/otn-pub/otn_software/autoupgrade.jar

vi download.cfg

cat download.cfg
# download.cfg
global.global_log_dir=/u01/app/oracle/stage/autoupgrade/log
global.keystore=/u01/app/oracle/stage/autoupgrade/keystore

patch1.folder=/u01/app/oracle/stage/autoupgrade/patch
patch1.patch=RU,DPBP,OPATCH
patch1.target_version=23

