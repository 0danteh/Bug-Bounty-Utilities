### How to use this oneliner:

1. You must have a list of parameters. To get the parameters, you need to use different other tools to manage to get them.
2. The parameters/endpoints must be named as `endpoints.txt` otherwise you can just change the name accordingly to what you have used.
3. This should help in finding specific terms within the endpoints that you can use to test for XSS, SQLi and so forth. Be catious with what you do, read the **Post Scriptum** note about this. Everything you do comes from a decision of yours, no one related to the development of this repo is involved.

**Note**: I'm using a codeblock for better vision from your side, however you can just copy it and paste it in the terminal and will work just as fine.

```sh
sort endpoints.txt | uniq > unique_endpoints.txt; grep "?" unique_endpoints.txt > parameterized_urls.txt; awk -F'[?&]' '{print $1 "?" $2}' parameterized_urls.txt | sort | uniq > sorted_params.txt; cut -d'?' -f1 parameterized_urls.txt | sort | uniq -c | sort -nr > grouped_urls.txt; while IFS= read -r url; do if [[ $url == *"id="* || $url == *"search="* || $url == *"page="* || $url == *"query="* ]]; then echo "$url"; fi; done < parameterized_urls.txt > injection_targets.txt; echo "Unique endpoints: unique_endpoints.txt"; echo "Parameterized URLs: parameterized_urls.txt"; echo "Sorted parameters: sorted_params.txt"; echo "Grouped URLs: grouped_urls.txt"; echo "Injection targets: injection_targets.txt"
```
