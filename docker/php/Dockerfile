# どのイメージを基に据え羽化
FROM php:7.3-fpm-alpine
# 作成したユーザの情報
LABEL maintainer="cha1ra"
# docker build コマンドで使う変数 --build-arg フラグを定義する
ARG TZ
# 環境変数 値
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
# docker build するときに実行される
RUN set -eux && \
#  apk add --update-cache --no-cache --virtual=.build-dependencies tzdata && \
#  cp /usr/share/zoneinfo/${TZ} /etc/localtime && \
#  apk del .build-dependencies && \
  docker-php-ext-install bcmath pdo_mysql && \
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
  composer config -g repos.packagist composer https://packagist.jp && \
  composer global require hirak/prestissimo


# set ... シェルの設定を確認、変更するコマンド
#  -e ... errexit パイプやサブシェルで実行したコマンドが1つでもエラーになったら直ちにシェルを終了する
#  -u ... nounset パラメータ展開中に設定していない変数があったらエラーとする
#  -x ... xtrace  トレース情報として、シェルが実行したコマンドとその引数を出力

# apk add ... Alpine Linux 上でパッケージインストールするため
# --update-cache ... リポジトリのキャッシュを更新する
# --no-cache ... パッケージキャッシュを使わない
# --virtual ... 仮の名前をつけてインストールすることができる
# だから --virtual=.build-dependencies を使って apk del .build-dependencies している
# tzdata ... Alpine Linux で タイムゾーンを設定するためのパッケージ

# docker-php-ext-install

