FROM hypriot/rpi-node

RUN mkdir /app
WORKDIR /app
ENV HTTP_PROXY=http://10.0.4.2:3128/
ADD package.json /app/package.json
RUN npm install && npm ls
RUN mv /app/node_modules /node_modules

ADD . /app

ENV PORT 80
EXPOSE 80

CMD ["node", "server.js"]
