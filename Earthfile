VERSION 0.8
PROJECT jahands/docker

prepare-workspace:
	FROM node:20-bookworm-slim
	WORKDIR /work

	RUN corepack prepare pnpm@latest-8 --activate
	RUN corepack enable pnpm

setup-project:
	FROM +prepare-workspace
	COPY package.json pnpm-lock.yaml .

install-deps:
	FROM +setup-project
	CACHE /pnpm-store
	RUN pnpm config set store-dir /pnpm-store
	RUN pnpm install --frozen-lockfile
