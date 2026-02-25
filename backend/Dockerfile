# ใช้ Node.js v18 (LTS) บน Alpine Linux เพื่อขนาดที่เล็ก
FROM node:18-alpine

# กำหนด working directory
WORKDIR /app

# คัดลอกไฟล์ package.json และ package-lock.json ก่อน (เพื่อใช้ Cache ของ Docker)
COPY package*.json ./

# ติดตั้ง dependencies
RUN npm install

# คัดลอกโฟลเดอร์ prisma และไฟล์ schema
COPY prisma ./prisma/

# คัดลอก Source code ทั้งหมด
COPY . .

# สร้าง Prisma Client
RUN npx prisma generate

# เปิด Port 3000
EXPOSE 3000

# คำสั่งรัน Server (รอ Database พร้อมก่อนค่อยรัน migrate ถ้าจำเป็น หรือรันใน compose)
CMD ["npm", "run", "dev"]