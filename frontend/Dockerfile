# --- Stage 1: Build ---
FROM node:20-alpine AS builder

WORKDIR /app

# Copy dependencies
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Build โปรเจกต์ (จะได้โฟลเดอร์ .output)
RUN npm run build

# --- Stage 2: Production Run ---
FROM node:20-alpine

WORKDIR /app

# Copy ไฟล์ที่ Build เสร็จแล้วจาก Stage 1
COPY --from=builder /app/.output ./.output

# กำหนด Environment Variables พื้นฐาน
ENV HOST=0.0.0.0
ENV PORT=3000

# เปิด Port
EXPOSE 3000

# รัน Nuxt Server
CMD ["node", ".output/server/index.mjs"]