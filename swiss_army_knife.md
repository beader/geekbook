# Swiss Army Knife

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