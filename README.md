

## Muthosamuel

Muthosamuel is a tool designed to find hidden subdomains and secrets present is either webpage, Github, and external javascripts present in the given URL.
This tool also finds S3 buckets, cloudfront URL's and more from those JS files which could be interesting like S3 bucket is open to read/write, or subdomain takeover and similar case for cloudfront.
It also scans inside given folder which contains your files.

## Cloud Storage Services Supported:
muthosamuel can find URL's for following cloud storage services:
```
1. Amazon AWS services (cloudfront and S3 buckets)
2. Digitalocean spaces 
3. Microsoft Azure 
4. Google Cloud Services 
5. Dreamhost 
6. RackCDN. 
```
## Secret Key's Searching: (beta)
Muthosamuel will also find secrets present in content of the page and javascripts files.
Those secret finding depends on some specific keywords and *Shannon Entropy* formula.
It might be possible that some secrets which searched by tool will be false positive.
This secret key searching is in beta and later version might have increased accuracy for search results.



## Installation Steps

1. Clone muthosamuel from git:
```
git clone https://github.com/muthosamuel/Muthosamuel Domain.git
```
2. Change the directory:
```
cd Muthosamuel Domain
```

3. Install the requirements:

```
pip3 install -r requirements.txt
```
4. Enjoy the Tool.

## Update to latest version:

Use following command to update to latest version:

```
git pull
```

## Usage

Short Form    | Long Form     | Description
------------- | ------------- |-------------
-u            | --url         | URL in which you want to find (sub)domains.
-l            | --listfile    | File which contain list of URL's needs to be scanned.
-o            | --output      | Output file name in which you need to save the results.
-c            | --cookie      | Cookies which needs to be sent with request.
-h            | --help        | show the help message and exit.
-cop          | --cloudop     | Give file name in which you need to store cloud services results.
-d            | --domains     | Give TLD (eg. for www.example.com you have to give example.com) to find subdomain for given TLD seperated by comma (no spaces b/w comma).
-g            | --gitscan     | Needed if you want to get things via Github too.
-gt           | --gittoken    | Github API token is needed, if want to scan (also needed -g also).
-gop	      | --gitsecretop | Saving secrets to a file found in github.
-k            | --nossl       | Use this to bypass the verification of SSL certificate.
-f            | --folder      | Root folder which contains files/folder.
-san          | --subject_alt_name    |  Find Subject Alternative Names for all found subdomains, Options: 'all', 'same'.

## SAN options description:
* all - This option will find all domains and subdomains.
* same - This will only find subdomains for specific subdomains.

## Examples

* To list help about the tool:
```
python3 muthosamuel.py -h
```
* To find subdomains, s3 buckets, and cloudfront URL's for given single URL:
```
python3 muthosamuel.py -u http://www.example.com
```
* To find subdomains from given list of URL (file given):
```
python3 muthosamuel.py -l list.txt
```

* To save the results in (output.txt) file:
```
python3 muthosamuel.py -u https://www.example.com -o output.txt
```
* To give cookies:
```
python3 muthosamuel.py -u https://www.example.com -c "test=1; test=2"
```
* To scan via github:
```
python3 muthosamuel.py -u https://www.example.com -o output.txt -gt <github_token> -g 
```
* No SSL Certificate Verification:
```
python3 muthosamuel.py -u https://www.example.com -o output.txt -gt <github_token> -g  -k
```
* Folder Scanning:
```
python3 muthosamuel.py -f /path/to/root/folder/having/files/and/folders/  -d example.com  -gt <github_token> -g  -k
```
* Subject Alternative Names:
```
python3 muthosamuel -u https://www.example -san all
```
* Saving secrets to a file scan found in github:
```
python3 muthosamuel.py -u https://www.example.com -o output.txt -gt <github_token> -g -gop filename_to_save
```








