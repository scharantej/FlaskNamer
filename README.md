 ```
# Import the necessary modules
from flask import Flask, render_template, request

# Create a Flask app
app = Flask(__name__)

# Define the home route
@app.route('/')
def home():
    return render_template('home.html')

# Define the generate route
@app.route('/generate', methods=['POST'])
def generate():
    # Get the user's input
    name = request.form.get('name')

    # Generate a new name
    new_name = generate_new_name(name)

    # Render the results page
    return render_template('results.html', new_name=new_name)

# Define the generate_new_name function
def generate_new_name(name):
    # Split the name into first and last name
    first_name, last_name = name.split(' ')

    # Get a random first and last name from the list of names
    new_first_name = random.choice(first_names)
    new_last_name = random.choice(last_names)

    # Return the new name
    return f'{new_first_name} {new_last_name}'

# Run the app
if __name__ == '__main__':
    app.run()
```

### HTML files

* home.html
* results.html

### Routes

* /: Home page
* /generate: Generate a new name