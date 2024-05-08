**IMPORTANT!!!**
You must follow `recon.md` first otherwise this won't work.

- It filters by `.js` files
- Run `SecretFinder` to look for keys -- remember to change the path as needed

```sh
grep ".js$" filterparam.txt | uro | anew jsfiles.txt && while read url; do python3 /../../SecretFinder/SecretFinder.py -i $url -o cli >> secret.txt; done < jsfiles.txt
```
with the premise you already have `filterparam.txt` from the `recon.md` oneliner
