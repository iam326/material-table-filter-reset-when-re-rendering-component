# Title

[material-table](https://material-table.com/#/) で再描画時にフィルターがリセットされてしまう現象への対処法。

## 問題となる現象

例えば、テーブルの行を選択した際に state が更新されるような実装がある場合、コンポーネントの再描画により、material-table のフィルターがリセットされてしまう。下記では、店舗のフィルターを設定した後、行を選択すると、店舗のフィルターが空になる。

![demo1](./demo-before.gif)

## 問題解決後

列の設定情報自体を state 化することで、上記の現象が発生しなくなる([commit](https://github.com/iam326/material-table-re-rendering-resets-the-filter/commit/4c86c53e04c150454fe34c9343f2b800261b3d3c))。

![demo2](./demo-after.gif)

## Environment

```
$ sw_vers
ProductName:    Mac OS X
ProductVersion: 10.15.6
BuildVersion:   19G2021

$ node --version
v12.18.2

$ npm --version
6.14.5

$ yarn --version
1.22.4

$ npm list --global --depth=0
├── create-react-app@3.4.1

$ yarn list --depth=0
├─ @material-ui/core@4.11.0
├─ material-table@1.68.0
├─ react-dom@16.13.1
├─ react@16.13.1
├─ typescript@3.7.5
```

## Usage

```
$ yarn install
$ yarn start
```

## Reference

* [material-table - Filtering states reset upon rerendering remote table](https://github.com/mbrn/material-table/issues/491)
