# ベースイメージを指定する
FROM ruby:3.0.3

# 必要なパッケージをインストールする
RUN apt-get update && \
  apt-get install -y \
  build-essential \
  libpq-dev \
  nodejs \
  yarn \
  curl \
  gnupg \
  dirmngr \
  imagemagick \
  libmagickwand-dev

# ルートディレクトリを作成する
RUN mkdir /app

# 作業ディレクトリを指定する
WORKDIR /app

# GemfileとGemfile.lockをコピーする
COPY Gemfile Gemfile.lock ./

# パッケージをインストールする
RUN gem install bundler && bundle install --jobs 4

# アプリケーションのコードをコピーする
COPY . .

# 環境変数を設定する
ENV RAILS_ENV=development

EXPOSE 3000

# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]
