
## Setup SSL multidomain Local Development

> [!NOTE]
> - OpenStreetMap use Leaflet js library that run only on HTTPS

1. Use Online Generator, example : https://certificatetools.com/
	- Add Common Name : `lebihcerdas.local`
	- Country Name : `ID`
	- State : `Jakarta`
	- Locality : `Jakarta`
	- Subject Alternate Names : 
		- Add DNS : `lebihcerdas.local`
		- Add DNS : `*.lebihcerdas.local`
	- CSR Options : `SHA256 - Self Sign - 1 Year(s)` 
	- Click SUBMIT
	
2. Save File to :
	- `C:\xampp\apache\conf\ssl.key\lebihcerdas.key`
	- `C:\xampp\apache\conf\ssl.crt\lebihcerdas.crt`
	
3. Edit file `C:\xampp\apache\conf\extra\httpd-ssl.conf`
   ```
   SSLCertificateFile "conf/ssl.crt/lebihcerdas.crt"
   SSLCertificateKeyFile "conf/ssl.key/lebihcerdas.key"
   ```
	
4. Restart Service Apache2

5. Install Certificate Windows
	- Run by type "cert", Control Panel -> "Kelola Setifikat Pengguna"
	- Trusted Root ... -> Certificates, right click -> All Task -> Import; select `lebihcerdas.crt`
    <br />
    <img width="348" alt="Install Certificate Windows" src="https://github.com/si294r/howto-wp/assets/10229458/c51f3f3b-42be-4eec-b5ec-9690a6408ea9">
    <br /><br />
    <img width="580" alt="Install Certificate Windows 2" src="https://github.com/si294r/howto-wp/assets/10229458/f8fdefbc-2fcc-4232-aeac-aa3b2f66ee09">

6. Restart Browser
