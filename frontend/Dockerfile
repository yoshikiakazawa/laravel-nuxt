# ベースイメージとしてNode.jsを使用
FROM node:18-alpine

# 作業ディレクトリの設定
WORKDIR /usr/src/app

# パッケージファイルをコンテナにコピー
COPY package*.json ./

# 依存関係のインストール
RUN npm install

# アプリケーションのコピー
COPY . .

# アプリケーションを起動
CMD ["npm", "run", "dev"]
