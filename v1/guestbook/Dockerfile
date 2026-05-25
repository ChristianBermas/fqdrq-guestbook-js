# FROM node:18-alpine
FROM node:18

WORKDIR /app

# Copy pre-installed dependencies
# COPY node_modules ./node_modules
COPY package*.json ./
RUN npm install
COPY . .

# Copy application source
COPY server.js ./
COPY public ./public/

# Create non-root user
# RUN addgroup -g 1001 -S nodejs && \
#     adduser -S nodeuser -u 1001
RUN groupadd -g 1001 nodejs && \
    useradd -u 1001 -g nodejs -m nodeuser

RUN chown -R nodeuser:nodejs /app
USER nodeuser

EXPOSE 3000
CMD ["node", "server.js"]
