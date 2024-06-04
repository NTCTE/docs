## Установка среды разработки PHP в Windows 10 или Windows 11

Для установки среды разработки PHP, ваши устройства должны поддерживать следующие характеристики:

1.  Паравиртуализация в BIOS
2.  Актуальные версии ОС (Windows 10, Windows 11, Ubuntu 22.*, Debian и т.п.)

## Настройка Windows

Для настройки Windows, необходимо установить и настроить WSL2 (Windows subsystem for Linux 2). Следуйте следующим шагам:

1.  Открыть терминал от имени администратора;
2.  Ввести команду:

```powershell
wsl --install
```

3.  После введения команды, необходимо установить [Ubuntu 22.* из Microsoft Store](https://apps.microsoft.com/detail/9pn20msr04dw?hl=en-US&gl=US).
4.  После установки, запустить Ubuntu 22.* и произвести первоначальную настройку Ubuntu 22.*.

## Настройка Ubuntu (WSL2)

После настройки WSL2 и установки Ubuntu 22.* или установки самой Ubuntu 22.*, необходимо произвести установку:

1.  PHP 8.* и всех необходимых модулей;
2.  MySQL, sqlite3;
3.  Composer.

Для настройки и установки данных пакетов, введите следующую команду в терминале:

```bash
$  sudo add-apt-repository -y ppa:ondrej/php && \
   sudo apt update && sudo apt upgrade -y && \
   sudo apt install -y openssl curl unzip mysql-server sqlite3 php8.3-{common,cli,bcmath,curl,mbstring,mysql,tokenizer,xml,zip,sqlite3} && \
   sudo curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php && \
   sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

После выполнения данной команды, все должно быть установлено.

## Настройка БД, установка СУБД

Для настройки базы данных необходимо произвести следующие настройки:

1.  Открыть установленную Ubuntu 22.* в режиме терминала;
2.  Ввести поочередно следующие команды:

```bash
$ sudo mysql
$ CREATE USER 'student'@'%' IDENTIFIED BY 'student';
$ CREATE DATABASE st;
$ GRANT ALL PRIVILEGES ON st.* TO 'student'@'%';
$ FLUSH PRIVILEGES;
$ EXIT;
```

3. Вышеприведенной командой был создан пользователь БД с логином `student` и паролем `student`; была создана база данных с именем `st`; пользователю `student` были выданы полные права на работу с БД `st`. 
4.  Установите СУБД HeidiSQL, перейдя  [по данной ссылке](https://www.heidisql.com/).

## Настройка Visual Studio Code

Теперь необходимо настроить VS Code для разработки на PHP, Laravel, а также для подключения к образу Ubuntu 22.* (нужно только для тех, кто работает через WSL2).

Для корректной настройки, необходимо установить следующие плагины в VS Code:

1.  [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)
2.  [IntelliCode API Usage Examples](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.intellicode-api-usage-examples)
3.  [Laravel Artisan](https://marketplace.visualstudio.com/items?itemName=ryannaddy.laravel-artisan)
4.  [Laravel Blade formatter](https://marketplace.visualstudio.com/items?itemName=shufo.vscode-blade-formatter)
5.  [Laravel Blade Snippets](https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-blade)
6.  [Laravel Blade Spacer](https://marketplace.visualstudio.com/items?itemName=austenc.laravel-blade-spacer)
7.  [Laravel Blade Wrapper](https://marketplace.visualstudio.com/items?itemName=IHunte.laravel-blade-wrapper)
8.  [Laravel Extension Pack](https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-extension-pack)
9.  [Laravel Extra Intellisense](https://marketplace.visualstudio.com/items?itemName=amiralizadeh9480.laravel-extra-intellisense)
10.  [Laravel goto view](https://marketplace.visualstudio.com/items?itemName=codingyu.laravel-goto-view)
11.  [laravel-goto-components](https://marketplace.visualstudio.com/items?itemName=naoray.laravel-goto-components)
12.  [laravel-jump-controller](https://marketplace.visualstudio.com/items?itemName=pgl.laravel-jump-controller)
13.  [PHP](https://marketplace.visualstudio.com/items?itemName=DEVSENSE.phptools-vscode)
14.  [PHP Debug](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug)
15.  [PHP Extension Pack](https://marketplace.visualstudio.com/items?itemName=xdebug.php-pack)
16.  [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)
17.  [PHP IntelliSense](https://marketplace.visualstudio.com/items?itemName=zobo.php-intellisense)
18.  [PHP Profiler](https://marketplace.visualstudio.com/items?itemName=DEVSENSE.profiler-php-vscode)

Для работы с VS Code в WSL2, необходимо установить [плагин WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl).

## Настройка Git в WSL2

Для настройки `git` в WSL2, введите в терминале следующие команды:

```bash
$ git config --global user.name "ВАШЕ ИМЯ"  
$ git config --global user.email "ВАШ EMAIL"
```
