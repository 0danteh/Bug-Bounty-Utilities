Automated Recon:

- Scan for subdomains (alive ones ofc)
- Params using waybackurls through `gau`
- Filtering of the params

```sh
subfinder -dL domains.txt -all -recursive -o subdomains.txt && cat subdomains.txt && httpx -l subdomains.txt -ports 443,80,8080,8000,8888 -threads 200 > alive_subdomains.txt && cat alive_subdomains.txt | gau > params.txt && cat params.txt | uro -o filterparam.txt
```
