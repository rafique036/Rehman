
# Stage 1: Install production dependencies
FROM node:22-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev



# Stage 2: Production runtime
FROM node:22-alpine AS runner
WORKDIR /app
ENV NODE_ENV=production
# Copy only production dependencies
COPY --from=deps /app/node_modules ./node_modules
# Copy application source code
COPY . .
EXPOSE 5001
CMD ["node", "src/server.js"]

