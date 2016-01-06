#Ambiente de Desenvolvimento com PHP

[![PHP](images/php.png)](#php) 
[![Apache](images/apache2.png)](#apache-24) 
[![GIT](images/git.png)](#git) 
[![Composer](images/composer.png)](#composer) 
[![PHPUnit](images/phpunit.png)](#phpunit) 
[![Selenium](images/seleniumhq.png)](#selenium) 
[![Xdebug](images/xdebug.png)](#xdebug)


#Para Windows 7

* Crie a pasta "C:\www"
* Crie a pasta "C:\Apache24"
* Crie a pasta "C:\php"
* Crie a pasta "C:\phpunit"
* Crie a pasta "C:\composer"

##PHP

Escolha a versão com "Thread Safe", que já vem o arquivo para usar com Apache:
Como informa o php.net: "With Apache you have to use the Thread Safe (TS) versions of PHP".

[Baixar PHP](http://windows.php.net/download)

Depois de baixar, desempacote os arquivos em C:\php

Nota: É fundamental que tenha instalado na sua máquina o VisualStudio
dependendo da versão do seu PHP VC9, VC11 ou VC14.
 

##Apache 2.4

[Baixar Apache 2.4](http://www.apachelounge.com/download)

Dica do php.net:

Por favor use o Apache compilado fornecido pelo [Apache Lounge](http://apachelounge.com).
Eles fornecem VC9, VC11 VC14 e compilações do Apache para x86 e x64.

Depois de baixar, desempacote os arquivos em C:\Apache24

###Arquivo de configurção do Apache

Procure o aquivo  "C:\Apache24\conf\httpd.conf".

####1) Para o Apache ler documentos PHP:

* PHP 7

		LoadModule php7_module "C:/php/php7apache2_4.dll"
		PHPIniDir "C:/php"
		AddHandler application/x-httpd-php .php

* PHP 5

		LoadModule php5_module "C:/php/php5apache2_4.dll"
		PHPIniDir "C:/php"
		AddHandler application/x-httpd-php .php

####2) Nome do servidor
Procure por:

		ServerName www.example.com:80

Altere para (Nome do servidor. Depois procure saber como configurar um virtual host):

		ServerName localhost:80

####3) Diretório Raiz para projetos

Procure por:

		DocumentRoot "c:/Apache24/htdocs"
		<Directory "c:/Apache24/htdocs">
		
Altere por:

		DocumentRoot "c:/www"
		<Directory "c:/www">
		
####4) Permitindo que arquivos .htaccess controlem suas directivas

Algo como:

		RewriteEngine On
		RewriteCond %{REQUEST_FILENAME} -d
		RewriteRule ^.*$ - [NC,L]
		RewriteRule ^(.*)$ %{ENV:BASE}index.php [NC,L]

Então, procure por:

		AllowOverride None
		
Alere para:

		AllowOverride All
		
####5) Descomentar a linha

		LoadModule rewrite_module modules/mod_rewrite.so
		
####6) Para ler arquivos index.html e index.html

Procure por:

		<IfModule dir_module>
			DirectoryIndex index.html
		</IfModule>
		
Altere para:
		
		<IfModule dir_module>
			DirectoryIndex index.html index.php
		</IfModule>	
		
###Rodar Apache

Digite o comando no CMD (Prompt de Comando)	:

	C:\Apache24\bin\httpd.exe -k install

	
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


