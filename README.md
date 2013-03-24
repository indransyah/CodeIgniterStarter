CodeIgniterStarter
==================

CodeIgniterStarter adalah CodeIgniter yang telah dikonfigurasi dengan
menggunakan Virtual Host dan telah memiliki URL yang user friendly.



### Mengapa menggunakan Virtual Host?

Virtual Host memungkinkan kita untuk mengubah URL localhost
(`http://localhost/namaproject`) menjadi nama domain tertentu
(`http://namaproject.com`) pada web server lokal kita. Dengan menggunakan
Virtual Host maka akan memudahkan kita ketika project tersebut diimplementasikan
di server (hosting).



### Maksudnya URL yang user friendly?

Secara default susunan URL CodeIgniter adalah
`http://namaproject.com/index.php/blog` hal ini sangatlah tidak user friendly
karena terdapat `index.php`. Susunan URL default CodeIgniter tersebut telah
diubah dengan menghilangkan` index.php` di CodeIgniterStarter ini.



### Konfigurasi

1.  Tambahkan domain yang ingin dijadikan Virtual Host di
    `C:\Windows\System32\drivers\etc\hosts`. Misal domain sebagai contoh adalah
    `www.codeigniterstarter.com`

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    127.0.0.1 www.codeigniterstarter.com
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

2.  Aktifkan Virtual Host di Apache (karena Virtual Host disable secara default)
    dengan menghilangkan tanda ## (uncomment) di depan `NameVirtualHost *:80`
    pada file `E:\xampp\apache\conf\extra\httpd-vhosts.conf`

3.  Tambahkan kode berikut di `httpd-vhosts.conf`*.*

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    <VirtualHost *:80>
        ServerAdmin admin@codeigniterstarter.com
        DocumentRoot "E:/xampp/htdocs/codeigniterstarter"
        ServerName www.codeigniterstarter.com
        ServerAlias www.codeigniterstarter.com
        ErrorLog logs/www.codeigniterstarter.com.log
        CustomLog logs/www.codeigniterstarter.com.log combined
        <Directory "E:/xampp/htdocs/codeigniterstarter">
            Options Indexes FollowSymLinks Includes ExecCGI
            AllowOverride All
            Order allow,deny
            Allow from all
            Require all granted
        </Directory>
    </VirtualHost>
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
	>   Ubah DocumentRoot dan Directory sesuai dengan path project
	>   
    >   Ubah ServerName dan ServerAlias sesuai domain yang dijadikan sebagai Virtual Host
    >   
    >   Yang lainnya optional

4.  Ubah base_url pada file configurasi CodeIgniter (`application\config\config.php`) sesuai dengan domain Virtual Host
    
	~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    $config['base_url']	= 'http://www.codeigniterstarter.com';
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
	
5.  Restart XAMPP


### Tested on

-   Windows 7

-   XAMPP 1.8.1

-   CodeIgniter 2.1.3