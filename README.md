Scrape is a general-purpose multi-threaded website scraper. Its primary purpose is to scrape websites for email addresses. Some of its special features include:

- Scraping email-name pairs from structured contact pages
- Identifying and handling Cloudflare pages
- Recursing until a stop pattern or 404 page is reached
- Flipping through site pages

Basic recurse and search for emails example:

    # ./Scrape --search-emails -r github.com
    [+] adding 1 url(s)
    [.] using user agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.16) Gecko/2009120208 Firefox/3.0.16 FBSMTWB
    [+] found email: privacy@github.com
    [+] found email: privacy@github.com
    [+] found email: privacy@github.com
    [+] found email: copyright@github.com.
    [+] found email: press@github.com
    [+] found email: press@github.com
    [+] found email: keplergo@mail.arc.nasa.gov
    [+] found email: keplergo@mail.arc.nasa.gov
    [+] found email: maxbrunsfeld@github.com
    [+] found email: atom@github.com
    [+] found email: atom@github.com

    ...

For a full list of features:

    $ ./Scrape -h
    usage: Scrape [-h] [-f FILE] [-r] [-d MAX_DEPTH] [-m MAX_RETRIES] [-p PAGES]
                  [--proxy PROXY] [-A USER_AGENT] [-t MAX_THREADS]
                  [-s STOP_PATTERN] [--stop-on-404] [--requeue-cloudflare]
                  [--recurse-pattern RECURSE_PATTERN] [--cross-domains] [-n]
                  [--search-regex SEARCH_REGEX] [--search-emails]
                  [--search-mailtos] [--email-names EMAIL_NAMES]
                  [--email-names-lines EMAIL_NAMES_LINES] [-o OUT_DIR]
                  [--include-non-html] [--out-urls OUT_URLS]
                  [--out-emails OUT_EMAILS] [--out-regex OUT_REGEX] [-D]
                  [url [url ...]]
    
    optional arguments:
      -h, --help            show this help message and exit
      -D, --debug           debug mode
    
    input options:
      -f FILE, --file FILE  url file
    
    spider options:
      -r, --recurse         recurse urls
      -d MAX_DEPTH, --max-depth MAX_DEPTH
                            max recursion depth (use with --recurse) (default: 3)
      -m MAX_RETRIES, --max-retries MAX_RETRIES
                            maximum number of times to retry a request (default:
                            0)
      -p PAGES, --pages PAGES
                            replace {page} in each url with a range of page
                            numbers. e.g. -p 1-2 -p 5,6-10
      --proxy PROXY         use proxy (supports http, https, socks4, and socks5
                            schemas)
      -A USER_AGENT, --user-agent USER_AGENT
                            user agent (default: random)
      -t MAX_THREADS, --max-threads MAX_THREADS
                            maximum number of threads to use at once (default: 6)
      -s STOP_PATTERN, --stop-pattern STOP_PATTERN
                            stop on pattern
      --stop-on-404         stop on 404
      --requeue-cloudflare  requeue cloudflare urls (useful with a rotating proxy)
      --recurse-pattern RECURSE_PATTERN
                            only recurse on urls matching one of these patterns
      --cross-domains       allow recursion to cross domains
      -n, --no-parent       don't touch parent urls
    
    search options:
      --search-regex SEARCH_REGEX
                            search for a custom regex (see also --out-regex)
      --search-emails       search for emails (see also --out-emails)
      --search-mailtos      search for emails in mailto: format
      --email-names EMAIL_NAMES
                            regex search for names with emails (good for spidering
                            structured contact lists)
      --email-names-lines EMAIL_NAMES_LINES
                            line numbers relative to each email address to search
                            for the name regex. this is useful for contact lists
                            (format: <start> [end])
    
    output options:
      -o OUT_DIR, --out-dir OUT_DIR
                            output directory for scraped pages (default: None)
      --include-non-html    include non-html files when downloading files
      --out-urls OUT_URLS   output file for scraped urls (intended for use with
                            recurse) (default: none)
      --out-emails OUT_EMAILS
                            output file for scraped emails (default: stdout)
      --out-regex OUT_REGEX
                            output file for custom regex (default: stdout)
      url                   urls
