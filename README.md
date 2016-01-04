#Ambiente de Desenvolvimento com PHP

[![PHP](images/php.png)](##PHP) 
[![Apache](images/apache.png)](#apache-24)  
[![GIT](images/git.png)](#git) 
[![Composer](images/composer.png)](#composer) 
[![PHPUnit](images/phpunit.png)](#phpunit) 
[![Selenium](images/seleniumhq.png)](#selenium) 
[![Xdebug](images/xdebug.png)](#xdebug)


#Para Windows 7

* Crie a pasta "C:\www"
* Crie a pasta "C:\Apache24"
* Crie a pasta "C:\php"

##PHP

Escolha a versão com "Thread Safe", que já vem o arquivo para usar com Apache:
Como informa o php.net: "With Apache you have to use the Thread Safe (TS) versions of PHP".

[Baixar PHP](http://windows.php.net/download)

Depois de baixar, desempacote os arquivos em C:\php

Nota: É fundamental que tenha instalado na sua máquina o VisualStudio
dependendo da versão do seu PHP VC9, VC11 ou VC14.
 

##Apache 2.4

[Baixar Apache 2.4](http://www.apachelounge.com/download)

Diga do php.net:

Por favor use o Apache compilado fornecido pelo [Apache Lounge](http://apachelounge.com).
Eles fornecem VC9, VC11 VC14 e compilações do Apache para x86 e x64.

Depois de baixar, desempacote os arquivos em C:\Apache24

####httpd.conf

Procure o aquivo  "C:\Apache24\conf\httpd.conf". Adicione as linhas seguintes.

		LoadModule php7_module "C:/php/php7apache2_4.dll"
		PHPIniDir "C:/php"
		AddHandler application/x-httpd-php .php


1) Nome do servidor
Procure por:

		ServerName www.example.com:80

Substitua por:

		ServerName localhost:80

2) Diretório Raiz para projetos

Procure por:

		DocumentRoot "c:/Apache24/htdocs"
		<Directory "c:/Apache24/htdocs">
		
Substitua por:

		DocumentRoot "c:/www"
		<Directory "c:/www">
		
3) Permitindo que arquivos .htaccess controlem suas directivas

Algo como no arquivo .htaccess:

		RewriteEngine On
		RewriteCond %{REQUEST_FILENAME} -d
		RewriteRule ^.*$ - [NC,L]
		RewriteRule ^(.*)$ %{ENV:BASE}index.php [NC,L]

Procure por:

		AllowOverride None
		
Substitua por:

		AllowOverride All
		
4) Descomentar a linha

		LoadModule rewrite_module modules/mod_rewrite.so
		
5) Adicionar se não existir a linha

		DirectoryIndex index.html index.php
		
##GIT
[Baixar installer GIT](https://git-for-windows.github.io)

##Composer


##PHPUnit


##Selenium


##Xdebug

[Baixar Xdebug](http://xdebug.org/download.php)

Adicione o arquivo baixado para "C:\php\ext\php_xdebug.dll"

Adicionar as linhas no arquivo php.ini

		[Zend Modules]
		zend_extension=php_xdebug.dll


