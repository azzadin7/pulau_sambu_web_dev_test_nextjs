# pulau_sambu_web_dev_test_nextjs
This project is a web dev test by PT Pulau Sambu using combination NextJS and Python

Setting Up the Environment
Install Node.js and npm: Next.js requires Node.js and npm (Node Package Manager).

Download and install from nodejs.org.
Install Python: Ensure you have Python installed.

Download and install from python.org.
Set Up a New Next.js Project:

Open your terminal and run:
bash
Copy code
npx create-next-app my-nextjs-app
cd my-nextjs-app
Set Up a Python Backend:

You can use frameworks like Flask or Django for your Python backend.
Creating the Next.js Frontend
Basic Structure: Your Next.js project will have the following structure:

bash
Copy code
my-nextjs-app
├── pages
│   ├── api
│   ├── _app.js
│   ├── index.js
├── public
├── styles
├── .gitignore
├── package.json
└── README.md
Creating Pages:

pages/index.js will be your main page. You can create other pages by adding files to the pages directory.
API Routes:

You can create API routes inside the pages/api directory. These will be serverless functions that can communicate with your Python backend.
Creating the Python Backend
Setting Up Flask:

Install Flask:
bash
Copy code
pip install Flask
Create a simple Flask app:
python
Copy code
# app.py
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api/data', methods=['GET'])
def get_data():
    return jsonify({"message": "Hello from Flask!"})

if __name__ == '__main__':
    app.run(debug=True)
Running the Flask App:

Start the Flask server:
bash
Copy code
python app.py
Connecting Next.js with Flask
Making API Calls from Next.js:

Install Axios for making HTTP requests:
bash
Copy code
npm install axios
Fetch data from your Flask backend:
javascript
Copy code
// pages/index.js
import axios from 'axios'
import { useEffect, useState } from 'react'

export default function Home() {
  const [data, setData] = useState(null)

  useEffect(() => {
    axios.get('http://localhost:5000/api/data')
      .then(response => {
        setData(response.data.message)
      })
      .catch(error => {
        console.error('Error fetching data:', error)
      })
  }, [])

  return (
    <div>
      <h1>Next.js with Python Backend</h1>
      <p>{data}</p>
    </div>
  )
}
CORS Handling:

Install Flask-CORS to handle Cross-Origin Resource Sharing:
bash
Copy code
pip install flask-cors
Update your Flask app to enable CORS:
python
Copy code
from flask_cors import CORS

app = Flask(__name__)
CORS(app)
Running the Applications
Run the Flask Backend:

bash
Copy code
python app.py
Run the Next.js Frontend:

bash
Copy code
npm run dev
Your Next.js frontend will be accessible at http://localhost:3000, and it will fetch data from your Flask backend running at http://localhost:5000
