FROM node:alpine AS builder

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: serve the built files
FROM nginx:alpine

# Copy built files from the builder stage
COPY --from=builder /app/dist /usr/share/nginx/html
# Or for Next.js: COPY --from=builder /app/.next /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]