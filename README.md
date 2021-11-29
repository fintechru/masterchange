# Мастеробмен

Мастеробмен - инструмент для проведения образовательных и исследовательских инициатив. 

## Возможности

- создание и редактирование кода смарт-контракта
- компиляция исходного кода смарт-контракта
- размещение смарт-контракта в удалённом узле Мастерчейн
- взаимодействие со смарт-контрактом в Мастерчейн

## Технологии

- JavaScript - скрипты взаимодействия с пользователем и удалённым узлом
- КриптоПро CSP - криптопровайдер для формирования транзакций

## Технические требования

Минимальные аппаратные требования:

- CPU / vCPU 2-х ядерный процессор с частотой более 2GHz
- RAM 8Гб
- HDD 50Гб


## Настройка окружения

- CryptoPro CSP - чтобы можно было делать ГОСТ-подписи, [Скачать](https://www.cryptopro.ru/products/csp/downloads) 

- Расширение для браузера - для взаимодействия с CryptoPro CSP, поддержка гарантирована для Сhromium GOST. Можно использовать Firefox или Chrome, но стабильная работа не гарантируется. [Скачать](https://www.cryptopro.ru/products/cades/plugin/get_2_0)

- Сhromium GOST - браузер для взаимодействия с сертифицированным СКЗИ, [Скачать](https://github.com/deemru/chromium-gost/releases)

- Контейнер с ключами - содержит контейнеры с сертификатами ключей, которые могут деплоить в сеть [Скачать](https://learn.fintechru.org/masterchange/keys.zip). Логие и пароль высылаются по запросу.

### Настройка окружения для Windows

- Каталоги с ключами копировать в AppData\Local\CryptoPro профиля пользователя

### Настройка окружения в Linux

#### Установка КриптоПро

Скачать RPM (для CentOS) или DEB (для Ubuntu) архив по ссылке: [Скачать](https://www.cryptopro.ru/products/csp/downloads#latest_csp50r2_linux)

```bash 
tar xzf linux-amd64.tgz
cd linux-amd64
```

или

```bash 
tar xzf linux-amd64_deb.tgz 
cd linux-amd64_deb
```

Затем sudo ./install.sh
Затем обязательно sudo yum install ./cprocsp-rdr-gui-gtk*.rpm или sudo dpkg -i cprocsp-rdr-gui-gtk*.deb

#### Установка расширения для браузера
Скачать архив "Linux 64 бита" со страницы https://www.cryptopro.ru/products/cades/downloads

```bash
tar xzf cades_linux_amd64.tar.gz
cd cades_linux_amd64
sudo yum install ./cprocsp-pki-cades*.rpm ./cprocsp-pki-plugin*.rpm или sudo dpkg -i cprocsp-pki-cades*.deb cprocsp-pki-plugin*.deb
```

#### Подготовка ключей
Скачать https://learn.fintechru.org/masterchange/keys.zip

```bash
unzip keys.zip
mkdir /var/opt/cprocsp/keys/$USER
mv 00s* /var/opt/cprocsp/keys/$USER
cd /var/opt/cprocsp/keys/$USER
for f in 00s*; do c=$(basename $f .000); done
/opt/cprocsp/bin/amd64/certmgr -inst -inst_to_cont -cont $c -f $c.000/$c.cer -at_signature
```

#### Настройка Сhromium GOST
Скачать RPM (для CentOS) или DEB (для Ubuntu) архив по ссылке:
https://github.com/deemru/chromium-gost/releases

```bash
sudo yum install chromium-gost-*-linux-amd64.rpm    # (для CentOS)
sudo dpkg -i chromium-gost-*-linux-amd64.deb       # (для Ubuntu)
```

# Содействие

Если вы встретили проблему, то смело создавайте [New Issue](https://github.com/fintechru/masterchange/issues/new) 

Если вы можете внести свой вклад в кодовую базу, улучшить определенный участок кода, то смело создавайте [Pull Request](https://github.com/fintechru/masterchange/pulls)
