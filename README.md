Laravel開発環境
===============

## Description

Laravelの開発環境をぽちぽちっとするだけで簡単に構築する奴。

## Usage

### Install

```shell
$ git clone https://github.com/kkznch/laravelvm.git
$ cd laravelvm
$ vagrant up --provision
```

### Settings

```shell
$ cd /path/to/laravelvm/shared
$ composer create-project laravel/laravel laravel --prefer-dist
```

### Check

以下のURLにアクセスできればOK。

http://192.168.16.132:9000
