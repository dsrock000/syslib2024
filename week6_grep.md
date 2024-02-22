# Grep command
## Getting started

This week we went over the **grep** command in Linux. It's a useful command for searching plain text data files and organizing results. I downloaded data from the Scopus database about cybersecurity articles. 

I downloaded information on the 15 articles with the most citations. I uploaded the scopus.bib file to my Linux server and ran various **grep** commands on the data. 

### Journals 

```
   grep "journal =" scopus.bib | cut -d"=" -f2 | \
     sed 's/ {//' | sed 's/},//' | \
     sort | uniq -c | sort
```

Results in:

```
      1 Computer
      1 Computers and Security
      1 Electronics (Switzerland)
      1 Future Generation Computer Systems
      1 IEEE Access
      1 IEEE Transactions on Smart Grid
      1 IT Professional
      1 Journal of Big Data
      1 Journal of Network and Computer Applications
      1 Nature Reviews Materials
      1 Pattern Recognition
      1 Proceedings of the 11th USENIX Security Symposium
      1 Proceedings of the 6th International Symposium on Information, Computer and Communications Security, ASIACCS 2011
      1 Proceedings of the IEEE
      1 SN Computer Science
```

### Number of citations

These 15 articles have been cited quite a few times! 

```
  grep -o "Cited by: [0-9]*" scopus.bib | \
    awk -F":" \
    'BEGIN { printf "Total Citations: "} \
    { sum += $2; } \
    END { print sum }'
```

Results in:

```
Total Citations: 13167
```

### Year of Publication 

I thought it would be a good test to come up with a command that sorted the year of publication for each of these journals. 

![image](https://github.com/dsrock000/syslib2024/blob/main/img/week6%20-%20grep4.png)



 
