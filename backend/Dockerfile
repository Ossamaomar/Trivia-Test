FROM node:alpine

WORKDIR /app

COPY package*.json ./

# install ALL deps for build
RUN npm ci

COPY . .

# build TS → JS
RUN npm run build

# remove dev deps
RUN npm prune --omit=dev

EXPOSE 3000

CMD ["node", "dist/server.js"]