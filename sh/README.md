## tools

- [shellcheck](https://github.com/koalaman/shellcheck): static analyzer for shell script written in Haskell
  - [wiki](https://github.com/koalaman/shellcheck/wiki) には shell script の gotchas が書かれているのでこちらも暇なときに目を通しておくといいかも


## memo

### 配列の処理

loop

```sh
arr=(a b c)

for i in ${arr[@]}
do
  ...
done
```

IFS(デフォルトは` `)で区切られた文字列の扱い

文字列から array への変換

```sh
arrlike="a b c d e"
arr=($arrlike)
```

IFSで区切られた文字列の繰り返し処理

IFSで区切られた文字列は `for` 文でループできる. 例えば jq コマンドは配列を IFS 区切りの文字列として返すので
返ってきた値をそのまま `for` 文に渡してループできる.

```sh

arrlike=$(curl -s -X GET https://example.com/foo.json | jq ....)

for i in $arrlike
do
  ...
done
```
