FROM node:lts-alpine as builder

RUN apk add --no-cache git python make g++

WORKDIR /app

RUN git clone https://github.com/AvapnoHelpingHand/DuckyAPI ./

RUN npm install --development   

FROM node:lts-alpine as app

ENV NODE_ENV development

RUN apk add --no-cache tini

WORKDIR /app
COPY --from=builder /app /app

EXPOSE 3030

ENTRYPOINT ["/sbin/tini", "--", "node", "index.js"]
CMD ["--config=config/development.env"]