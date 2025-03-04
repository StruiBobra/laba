# Волобуев Руслан К-ИСП-39-2

***

Установил гостивые дополнения для копирование текст с пк на ВМ.

## 1 Задание

Установка `wget`

```bash
sudo yum install wget
```

`wget` — это мощная утилита командной строки, предназначенная для загрузки файлов с интернета. Она работает через протоколы HTTP, HTTPS и FTP, позволяя пользователям скачивать файлы как интерактивно, так и в фоновом режиме.

![изображение](https://github.com/user-attachments/assets/c2f5317c-5ba0-46ac-86c2-32cd7d94387a)


## 2 Задание

Установка `curl`
```bash
sudo yum install curl
```

`curl` — это инструмент для передачи данных с сервера или к серверу через URL.

![изображение](https://github.com/user-attachments/assets/30e2d0bb-c10d-4381-84eb-142a6d9f605f)

---

Команда загружает файл репозитория Docker `docker-ce.repo` с официального сайта Docker и помещает его в каталог `/etc/yum.repos.d/`

```bash
sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo
```

![изображение](https://github.com/user-attachments/assets/176b8997-0100-4bae-87c6-ac2d8485eaf4)


Установка `Docker`
 
 ```bash
sudo yum install docker-ce docker-ce-cli containerd.io
```
  
![изображение](https://github.com/user-attachments/assets/793b3543-a0ad-445c-9a2d-431ccfaeb271)


Запуск службы `Docker`

Запуск службы `Docker` и включаем её в автозапуск. 
Команда:
 ```bash
sudo systemctl enable docker --now
```

![изображение](https://github.com/user-attachments/assets/14499568-000a-41bc-ad9e-af5a89bfdf71)


## 3 Задание

---

Этой уомандой я получил последнию версию `Docker Compose`
Команда:
```bash
COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)
```
  
![изображение](https://github.com/user-attachments/assets/93084380-6900-4d1a-9b9c-4ba65a481d5b)

---

Скачивание и установка Docker Compose

Команда загружает бинарный файл `Docker Compose` из `GitHub Releases` для операционной системы, а затем сохраняет его в `/usr/bin/docker-compose`

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
```

![изображение](https://github.com/user-attachments/assets/3f7ce01d-f9ef-4637-b562-fd8108ec460e)

---

### 3. Проверка установленной версии `Docker Compose`


Команда даёт файлу `/usr/bin/docker-compose` право на выполнение, делая его полноценной программой, которую можно запускать из командной строки.

```bash
sudo chmod +x /usr/bin/docker-compose
```

Проверяю версию `Docker Compose`:
```bash
docker-compose --version
```

![изображение](https://github.com/user-attachments/assets/a90033fc-65a1-4456-8c51-3dba5a84e794)

---

Клонирую репозиторий с конфигурацией `Grafana`

Устанавливаю Git:
```bash
sudo yum install git
```

Клонирую репозиторий
```bash
git clone https://github.com/skl256/grafana_stack_for_docker.git
```

![изображение](https://github.com/user-attachments/assets/33293314-a88e-44a5-a2b6-c671454095c6)

---

Создаем необходимые директории и файлы (рис. 4):

Создает папку в директории `/mnt/common_volume/swarm/grafana/config`
```bash
sudo mkdir -p /mnt/common_volume/swarm/grafana/config
```

Создаем директории `grafana-config` `grafana-data` `prometheus-data`:
```bash
sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}
```

Меняем владельца для дерикторий

```bash
sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}
```

![изображение](https://github.com/user-attachments/assets/7d55b23d-acb8-4564-a5c0-ce48d473b98a)

Создаем новый пустой файл:
```bash
touch /mnt/common_volume/grafana/grafana-config/grafana.ini
```

Копирование всх файлов из `config/*` в `/mnt/common_volume/swarm/grafana/config/`
```bash
cp config/* /mnt/common_volume/swarm/grafana/config/
```

Переименовываю файл:
```bash
mv grafana.yaml docker-compose.yaml
```

![изображение](https://github.com/user-attachments/assets/30d2ecef-8ec3-43ee-8f06-ab13b32de593)

---

Запускаю `Docker`

Запускаем контейнеры Docker. Docker запускается в фоновом режиме, это дедает ключ `-d`:

```bash
sudo docker compose up -d
```

![изображение](https://github.com/user-attachments/assets/8608f225-3154-4795-a760-eb2571eaa350)


---

## 4 Задание

Команда для запуска `Docker`
```bash
sudo docker compose up -d
```

Данная команда останавливает все контейнеры которые были запущины до этого:
```bash
sudo docker compose stop
```

![изображение](https://github.com/user-attachments/assets/04be50be-b8df-4d71-ac27-b7648f1db4fe)


---

Данная команда удаляет все контейнеры которые были запущины до этого:
```bash
sudo docker compose down
```

![изображение](https://github.com/user-attachments/assets/3e631efe-eab3-49ae-9710-582ece81fd06)

---

Данная команда показывает статус всех контейнеров которые были запущины до этого:
```bash
sudo docker compose ps
```

![изображение](https://github.com/user-attachments/assets/616a08a3-0a53-45dd-a117-0f6436ce72aa)


---

Клонирует папку из указанной репозитории:
```bash
git clone https://github.com/StruiBobra/laba.git 
```

![изображение](https://github.com/user-attachments/assets/8f08ef5a-9ba4-4fa8-9506-4b274a899b1d)


---

Команда:
```bash
pwd
```

`pwd` (от англ. print working directory — вывести текущую директорию) — это команда в Unix-подобных операционных системах (например, Linux и macOS), которая показывает путь к текущей рабочей директории, в которой вы находитесь в данный момент в терминале.

![изображение](https://github.com/user-attachments/assets/e43c21a9-2ded-4966-9f7f-8d0a5e69e13e)

---

Делаем бэкап фала `docker-compose.yaml` и перемещаем только что клонированный файл в папку `grafana_stack_for_docker`:

```bash
mv laba/prometheus.yaml ./
mv laba/docker-compose.yaml ./
```

Бэкап (от англ. backup — резервное копирование) — это процесс создания дополнительной копии данных для их восстановления в случае потери.


![изображение](https://github.com/user-attachments/assets/671b8768-2308-40cc-bc95-31e9ac794a38)


## 5 Задание

Делаем бэкап фала `prometheus.yaml` который находится в `/mnt/common_volume/swarm/grafana/config/`

Перед тем как перемещать файл `prometheus.yaml` в `/mnt/common_volume/swarm/grafana/config/` нужно сначало остановить все контейнеры через команду `sudo docker compose stop`

![изображение](https://github.com/user-attachments/assets/39de7189-73e6-4748-97a0-0c93c26c68ff)

После этого можно спокойно перемещать файл `prometheus.yaml` в `/mnt/common_volume/swarm/grafana/config/` 
```bash
sudo mv prometeus.yaml /mnt/common_volume/swarm/grafana/config/
```

![изображение](https://github.com/user-attachments/assets/d0dd5354-6aca-4e6f-b53e-b06454581d94)


Теперь нужно поднять `Docker` командой `sudo docker compose up -d` для того чтобы зайти в интерфейс через браузер.

Для того чтобы зайти нужно прописать в поиске `localhost:3000`
Теперь нужно создать `Dashboards` - Информационные панели



