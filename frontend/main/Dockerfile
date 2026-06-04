FROM node:22-alpine AS base
WORKDIR /frontend
COPY package*.json .
RUN npm install

FROM base AS build
WORKDIR /frontend
COPY --from=base . /node_modules
COPY . .
RUN npm run build


FROM build AS run
WORKDIR /frontend
COPY --from=build  . /build

EXPOSE 4030

CMD ["npm","run","start"]