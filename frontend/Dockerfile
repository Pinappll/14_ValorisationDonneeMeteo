FROM dhi.io/node:24-debian13-dev AS build

WORKDIR /app

COPY package*.json .
RUN npm install --legacy-peer-deps && \
    npm install pinia echarts vue-echarts --legacy-peer-deps

COPY . .
RUN npm run build

FROM dhi.io/node:24-debian13

WORKDIR /app

COPY --from=build /app/.output /app/.output

ENV NODE_ENV=production

EXPOSE 3000

CMD ["node", ".output/server/index.mjs"]
