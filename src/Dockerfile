FROM node:18.15-buster-slim AS build
ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini
WORKDIR /app
COPY package*.json ./
RUN --mount=type=cache,target=/app/.npm \
  npm set cache /app/.npm && \
  npm ci --only=production --ignore-scripts
COPY . .

FROM node:18.15-buster-slim 
ENV NODE_ENV=production
ENV TZ=UTC
EXPOSE 8080
COPY --from=build /tini /tini
USER node
WORKDIR /app
COPY --chown=node:node --from=build /app/node_modules ./node_modules
COPY --chown=node:node --from=build /app .
ENTRYPOINT ["/tini", "--"]
CMD ["node", "server"]