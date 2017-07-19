`rsync -a = rsync -rlptgoD`

`rsync -av = rsync -rlptgoDv`

`rsync -av --checksum = rsync -rlptgoDvc`

[vagrant@localhost ~]$ ansible -i hosts localhost -m shell -a "rsync -rlpgoDvc --bwlimit=8192 --links --delete -n hexo _base/ ~/dest/"

```
localhost | SUCCESS | rc=0 >>
sending incremental file list

sent 366453 bytes  received 1619 bytes  147228.80 bytes/sec
total size is 57094308  speedup is 155.12 (DRY RUN)
```

[vagrant@localhost ~]$ ansible -i hosts localhost -m shell -a "rsync -rlptgoDvc --bwlimit=8192 --links --delete -n hexo _base/ ~/dest/"

```
localhost | SUCCESS | rc=0 >>
sending incremental file list
（省略）
wget-1.11.4-1-bin/share/locale/es/
wget-1.11.4-1-bin/share/locale/es/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/et/
wget-1.11.4-1-bin/share/locale/et/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/eu/
wget-1.11.4-1-bin/share/locale/eu/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/fi/
wget-1.11.4-1-bin/share/locale/fi/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/fr/
wget-1.11.4-1-bin/share/locale/fr/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/ga/
wget-1.11.4-1-bin/share/locale/ga/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/gl/
wget-1.11.4-1-bin/share/locale/gl/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/he/
wget-1.11.4-1-bin/share/locale/he/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/hr/
wget-1.11.4-1-bin/share/locale/hr/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/hu/
wget-1.11.4-1-bin/share/locale/hu/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/id/
wget-1.11.4-1-bin/share/locale/id/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/it/
wget-1.11.4-1-bin/share/locale/it/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/ja/
wget-1.11.4-1-bin/share/locale/ja/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/nb/
wget-1.11.4-1-bin/share/locale/nb/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/nl/
wget-1.11.4-1-bin/share/locale/nl/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/pl/
wget-1.11.4-1-bin/share/locale/pl/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/pt/
wget-1.11.4-1-bin/share/locale/pt/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/pt_BR/
wget-1.11.4-1-bin/share/locale/pt_BR/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/ro/
wget-1.11.4-1-bin/share/locale/ro/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/ru/
wget-1.11.4-1-bin/share/locale/ru/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/sk/
wget-1.11.4-1-bin/share/locale/sk/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/sl/
wget-1.11.4-1-bin/share/locale/sl/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/sr/
wget-1.11.4-1-bin/share/locale/sr/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/sv/
wget-1.11.4-1-bin/share/locale/sv/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/tr/
wget-1.11.4-1-bin/share/locale/tr/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/uk/
wget-1.11.4-1-bin/share/locale/uk/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/vi/
wget-1.11.4-1-bin/share/locale/vi/LC_MESSAGES/
wget-1.11.4-1-bin/share/locale/zh_CN/
wget-1.11.4-1-bin/share/locale/zh_CN/LC_MESSAGES/
（省略）

sent 366453 bytes  received 1619 bytes  147228.80 bytes/sec
total size is 57094308  speedup is 155.12 (DRY RUN)
```

