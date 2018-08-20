#Ambiente de Desenvolvimento com PHP

[![PHP](images/php.png)](#php) 
[![Apache](images/apache2.png)](#apache-24) 
[![GIT](images/git.png)](#git) 
[![Composer](images/composer.png)](#composer) 
[![PHPUnit](images/phpunit.png)](#phpunit) 
[![Selenium](images/seleniumhq.png)](#selenium) 
[![Xdebug](images/xdebug.png)](#xdebug)


# Para Windows 7

* Crie a pasta "C:\www"
* Crie a pasta "C:\Apache24"
* Crie a pasta "C:\php"
* Crie a pasta "C:\phpunit"
* Crie a pasta "C:\composer"

## PHP

Escolha a versão com "Thread Safe", que já vem o arquivo para usar com Apache:
Como informa o php.net: "With Apache you have to use the Thread Safe (TS) versions of PHP".

[Baixar PHP](http://windows.php.net/download)

Nota: É fundamental que tenha instalado na sua máquina o VisualStudio
dependendo da versão do seu PHP VC9, VC11 ou VC14.

* Depois de baixar, desempacote os arquivos em "C:\php"

* Tornando o PHP executável pela linha de comando.

Abra o Prompt de Comando como Administrador, e execute o comando:
		
		SETX PATH "%PATH%;C:\php;" -m

* Para testar, digite o comando na linha de comando:

```bash
php --version
```

## Apache 2.4

[Baixar Apache 2.4](http://www.apachelounge.com/download)

Dica do php.net:

Por favor use o Apache compilado fornecido pelo [Apache Lounge](http://apachelounge.com).
Eles fornecem VC9, VC11 VC14 e compilações do Apache para x86 e x64.

Depois de baixar, desempacote os arquivos em C:\Apache24

### Arquivo de configurção do Apache

Abre o aquivo  "C:\Apache24\conf\httpd.conf". Agora siga as instruções abaixo para alterá-lo:

#### 1) Para o Apache ler documentos PHP

* PHP 7

		LoadModule php7_module "C:/php/php7apache2_4.dll"
		PHPIniDir "C:/php"
		AddHandler application/x-httpd-php .php

* PHP 5

		LoadModule php5_module "C:/php/php5apache2_4.dll"
		PHPIniDir "C:/php"
		AddHandler application/x-httpd-php .php

#### 2) Nome do servidor

Procure por:

		ServerName www.example.com:80

Altere para (Nome do servidor. Depois procure saber como configurar um virtual host):

		ServerName localhost:80

#### 3) Diretório raiz para projetos

Procure por:

		DocumentRoot "c:/Apache24/htdocs"
		<Directory "c:/Apache24/htdocs">
		
Altere para:

		DocumentRoot "c:/www"
		<Directory "c:/www">
		
#### 4) Permitindo que arquivos .htaccess controlem suas directivas

Coisas como, exemplo:

		RewriteEngine On
		RewriteCond %{REQUEST_FILENAME} -d
		RewriteRule ^.*$ - [NC,L]
		RewriteRule ^(.*)$ %{ENV:BASE}index.php [NC,L]

Então, procure por:

		AllowOverride None
		
Altere para:

		AllowOverride All
		
Agora, descomente a linha:

		LoadModule rewrite_module modules/mod_rewrite.so
		
#### 5) Para ler arquivos index.html e index.html

Procure por:

		<IfModule dir_module>
			DirectoryIndex index.html
		</IfModule>
		
Altere para:
		
		<IfModule dir_module>
			DirectoryIndex index.html index.php
		</IfModule>	
		
### Executando Apache e incluindo na lista de serviços do Windows

Digite o comando no CMD (Prompt de Comando) como Administrador:

		C:\Apache24\bin\httpd.exe -k install

### Testando Apache

Para ver se funcionou, verifique se o Apache2.4 está na lista de serviços local do Windows.

* Pressione Windows+R
* Digite, services.msc
* Procure por Apache2.4

Agora digite no seu Navegador http://localhost.

	
##GIT
[Baixar installer GIT](https://git-for-windows.github.io)


## Instalar Composer

No link abaixo procure como instalar no Windows

[Baixar Composer](https://getcomposer.org/download/)


## PHPUnit

[Baixar o arquivo phpunit.phar](http://https://phpunit.de/)

* Adicione o arquivo baixado phpunit.phar, na pasta "C:\phpunit\"
* Crie um arquivo com a extensão .bat "phpunit.bat"
* Adicione o código seguinte no arquivo "phpunit.bat":
	
		@ECHO OFF
		SET BIN_TARGET=%~dp0/phpunit.phar
		php "%BIN_TARGET%" %*

* Tornando o PHPUnit executável pela linha de comando.

Abra o Prompt de Comando como Administrador, e execute o comando:
		
		SETX PATH "%PATH%;C:\phpunit;" -m

* Para testar, digite o comando na linha de comando:

```bash
phpunit --version
```

## Selenium

[Baixar Selenium Server](http://docs.seleniumhq.org/download/)

[Testes com PHPUnit e Selenium 2](https://github.com/roggeo/phpunit-selenium-2)

[Exemplos](https://github.com/giorgiosironi/phpunit-selenium/)


## Xdebug

[Baixar Xdebug](http://xdebug.org/download.php)

Adicione o arquivo baixado para "C:\php\ext\php_xdebug.dll"

Adicionar as linhas no arquivo php.ini

		[Zend Modules]
		zend_extension=php_xdebug.dll


**Ok tudo pronto**
