FROM node:23-alpine AS production

ENV NODE_ENV=production
ENV NODE_OPTIONS=--openssl-legacy-provider

WORKDIR /usr/src/client

COPY package*.json .

RUN npm install

# Install TypeScript globally
RUN npm install -g typescript pm2

COPY . .     
# Copy all files from the current directory which is all the files in the api to the WORKDIR  first . means current directory second . means the WORKDIR

RUN npm run build 
# This command will run the build script in the package.json file

EXPOSE 8081
# Expose port 8081 to the outside world this is the port that the api will run on

# CMD ["npm", "start"]
CMD ["sh", "-c" , "npm run start:production"]