FROM node:20-alpine

WORKDIR /app

COPY package* .
COPY ./prisma .
RUN npm install
RUN npx prisma generate
# these things change very rarely so ideally we should cache them because
COPY . .
# first dot refers to the dir where we execute docker build, 
# second dot refers to /app

RUN npm run build

EXPOSE 3000

CMD ["node", "dist/index.js"]
# RUN commands run when you build the image
# CMD runs when you start the container.