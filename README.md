# DevTinder

- Create a Vite + React application
- Remove unnecessary code and create a Hello World App
- Install Tailwind CSS
- Add Navbar component to App.jsx
- Create a NavBar.jsx Component
- Installed React router dom

Body
    Navbar
    Route=/  => Feed
    Route=/login  => Login
    Route=/connections  => Connections
    Route=/profile  => Profile

- Create BrowserRouter > Routes > Route=/ Body > RouteChildren
- Creates Footer 

- Creates a Login Page 
- Install axios
- Install cors in backend => add middleware to with configurations : origin , credentials : true 
- Whenever you're making API call so pass axios => {withCredentials: true}
- Install Redux Toolkit
- install react-redux + @reduxjs/toolkit => configureStore => Provider => createSlice => add reducer to store 
- Add redux Devtools in chrome 
- Login and see if your data is comming properly in the store
- Navbar should update as soon as user logs in
- Refactor our code to add constants file + create a components folder
- You should not be access other routes without login 
- If token is not present , redirects user to login page 
- Logout
- Get the feed and add the feed in the store
- Profile page
- Edit profile feature 
- Show toast Message on sava a profile
- see all my connctions (accepted)
- new page - see all my connection requests
- Feature - Accept / Reject Connection Request
- Send/Ignore the user card from the feed


# Deployment

- SignUp on AWS
- Launch Instance
- chmod 400 <secret>.pem
- Connected to the machine using SSH command 
ssh -i "devTinder-secret.pem" ubuntu@ec2-43-204-231-23.ap-south-1.compute.amazonaws.com
- Install node version
- Git clone

# Frontend
   - npm install
   - npm run build
   - sudo apt update
   - sudo apt install nginx
   - sudo systemctl start nginx
   - sudo systemctl enable nginx
   - sudo scp -r dist/* /var/www/html/
   - Enable port :80 of your instance

# Backend
   - updated DB password
   - allowed ec2 instance public IP on mongo server
   - npm install pm2 -g
   - pm2 start npm --name "devtinder-backend" -- start
   - pm2 logs , pm2 flush <name> , pm2 delete <name>
   - config nginx - /etc/nginx/sites-available/default
   - restart nginx - sudo systemctl restart nginx
   - Modify the BASEURL in frontend project to "/api"

# Nginx Config

Frontend - http://43.204.231.23/
Backend - http://43.204.231.23:3000

Domain name = devtinder.com => 43.204.231.23

Frontend = devtinder.com
Backend =  devtinder.com:7777 => devtinder.com/api


# nginx config :

  server_name 43.204.231.23

  location /api/ {
        proxy_pass http://localhost:3000/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }