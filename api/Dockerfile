# Stage 1: Build the application
FROM node:14 AS builder

WORKDIR /usr/src/app

# Copy package.json and package-lock.json to install dependncies
COPY package*.json ./

# Install dependencies (only for production to keep the size small)
RUN npm install --only=production

COPY . .


# Stage 2: Use a smaller image for production
FROM node:14-alpine AS production

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app ./

EXPOSE 300

CMD ["npm","start"]