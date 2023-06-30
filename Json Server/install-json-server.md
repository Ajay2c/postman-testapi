There are times when you are creating a software or a part of software that relies on network requests but your backend infrastructure isn’t ready yet. What do you typically do?

Build the component without any network calls?
Build the component using dummy data?
Whilst 2 is better than 1, they are both ultimately inefficient and make you work twice as much.

**Introducing JSON Server**
Step 1: To set up the JSON Server run the following command:

$npm install -g json-server

Step 2: Create a db.json file with some data
{
 “posts”: [
 { “id”: 1, “title”: “learn json-server”, “author”: “Mrinmay Mukherjee” }
 ],
 “comments”: [
 { “id”: 1, “body”: “it's pretty awesome”, “postId”: 1 }
 ],
 “profile”: { “name”: “Mrinmay Mukherjee” }
}
Step 3: Start JSON Server
$json-server --watch db.json --port 8000

This runs a local server on port 8000, and watches the db.json file for any changes. In case anything changes, the server restarts itself and the changes are automatically and safely saved to db.json

That’s it. You can now start making GET, POST, PUT, PATCH or DELETE calls to your mock server and build the necessary components all the way such that the only thing left to do once backend infrastructure is up and running, would be to replace the localhost url with the production url.

**Examples of GET and POST:**
GET
fetch(‘http://localhost:8000/posts/')
 .then(response => response.json())
 .catch(error => console.error('Error:', error))
 .then(response => console.log('Success:', JSON.stringify(response)));
2. POST

let data = { 
  “id”: 10, 
  “title”: “json-server is not bad. It's great!”, 
  “author”: “Dwight Shrute” 
}

 fetch(‘http://localhost:3000/posts/', {
 method: “POST”,
 headers: {
 “Content-Type”: “application/json”,
 },
 body: JSON.stringify(data),
 })
 .then(response => response.json())
 .catch(error => console.error(‘Error:’, error))
 .then(response => console.log(‘Success:’, JSON.stringify(response)));
JSON Server is an exceptional library and it’s utilities go way beyond whatever was mentioned in this article. I encourage everyone to read their
