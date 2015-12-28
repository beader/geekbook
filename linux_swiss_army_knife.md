# Swiss Army Knife

## Tools

### du

du - estimate file space usage

```zsh
# estimate the total size of dir
# -s, --summarize display only a total for each argument
# -h, --human-readable print sizes in human readable format
# -c, --total produce a grand total
du -shc dir
```

### pup

[pup](https://github.com/EricChiang/pup) is a command line tool for processing HTML. It reads from stdin, prints to stdout, and allows the user to filter parts of the page using CSS selectors.

```zsh
curl -s https://news.ycombinator.com/ | pup 'table table tr:nth-last-of-type(n+2) td.title a'
```

### jq

[jq](https://stedolan.github.io/jq/) is like sed for JSON data - you can use it to slice and filter and map and transform structured data with the same ease that sed, awk, grep and friends let you play with text.

```zsh
curl 'https://api.github.com/repos/stedolan/jq/commits?per_page=5' | jq '.[0] | {message: .commit.message, name: .commit.committer.name}'
```

### xargs

[xargs](http://linux.die.net/man/1/xargs) build and execute command lines from standard input.

```zsh
# download all pdfs from a website
URL='https://www.cs.ox.ac.uk/people/nando.defreitas/machinelearning/' curl -s $URL | pup 'a attr{href}' | grep pdf | xargs -I {} wget $URL{}
```

[Intro to xargs](https://www.youtube.com/watch?v=8kAB_VgokMY)

### parallel

GNU [parallel](https://www.gnu.org/software/parallel/) is a shell tool for executing jobs in parallel using one or more computers.

### example - 获取台北RAW餐厅可预订时段信息

```zsh
PEOPLE=4; START_DATE='2015-12-24'; URL='https://api.eztable.com/v3/restaurants/2128/quotas?date=%s&people=%s&premium=true\n'; seq 0 10 | xargs -I {} date -d $START_DATE" {} days" +%Y-%m-%d | xargs -I {} printf $URL {} $PEOPLE | parallel "curl -s {} | jq '.premium_quotas[] | select(.availability==true) | {datetime: .datetime, purchase_link: .purchase_link}'"
```