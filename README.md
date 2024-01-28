# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)

    Source code link: https://www.tutussfunny.com/react-with-asp-net-core-web-api-full-stack-crud-application/
    Video link: React with Asp.Net Core web Api Full Stack Crud Application

    React with Asp.Net Core web Api Full Stack Crud Application
    Ø Create database objects
    Ø Create Backend using .NET Core web API
    Ø Create React js project

Backend
Nugget packages:
• EntityFrameworkCore.Design 7.0.1
• EntityFrameworkCore.SqlServer 7.0.1
• EntityFrameworkCore.Tools 7.0.1
• Newtonsoft.Json 13.0.2
###Check these in dependencies > packages
Sql server and sql ssms: https://www.sqlservertutorial.net/install-sql-server/
Connect server to ssms: https://www.sqlservertutorial.net/connect-to-the-sql-server/
Server name: DESKTOP-49ELLTT\sa
Password: 123
PM> add-migration initial
PM> update-database
npx create-react-app aspcrud-frontend
cd aspcrud-frontend
npm start
Bootstrap: getbootstrap.com/docs/4.0/components/forms/
Copy paste from first link: StudentCrud.js
******************************\_\_\_\_******************************
<h1>Student Details</h1>
<div class="container mt-4">
<form>
<div class="form-group">
<input
type="text"
class="form-control"
id="id"
hidden
value={id}
onChange={(event) => {
setId(event.target.value);
}}
/>
<label>Student Name</label>
<input
type="text"
class="form-control"
id="stname"
value={stname}
onChange={(event) => {
setName(event.target.value);
}}
/>
</div>
<div class="form-group">
<label>Course</label>
<input
type="text"
class="form-control"
id="course"
value={course}
onChange={(event) => {
setCourse(event.target.value);
}}
/>
</div>
<div>
<button class="btn btn-primary mt-4" onClick={save}>
Register
</button>
<button class="btn btn-warning mt-4" onClick={update}>
Update
</button>
</div>
</form>
</div>
<br></br>
<table class="table table-dark" align="center">
<thead>
<tr>
<th scope="col">Student Id</th>
<th scope="col">Student Name</th>
<th scope="col">Course</th>
<th scope="col">Option</th>
</tr>
</thead>
{students.map(function fn(student) {
return (
<tbody>
<tr>
<th scope="row">{student.id} </th>
<td>{student.stname}</td>
<td>{student.course}</td>
<td>
<button
type="button"
class="btn btn-warning"
onClick={() => editStudent(student)} >
Edit
</button>
<button
type="button"
class="btn btn-danger"
onClick={() => DeleteStudent(student.id)} >
Delete
</button>
</td>
</tr>
</tbody>
);
})}
</table>
From <https://www.tutussfunny.com/react-with-asp-net-core-web-api-full-stack-crud-application/?expand_article=1>
******************************\_\_\_\_******************************
Above this add the function as well
******************************\_\_\_\_******************************
const [id, setId] = useState("");
const [stname, setName] = useState("");
const [course, setCourse] = useState("");
const [students, setUsers] = useState([]);
useEffect(() => {
(async () => await Load())();
}, []);
async function Load() {
const result = await axios.get("https://localhost:7195/api/Student/GetStudent");
setUsers(result.data);
console.log(result.data);
}
async function save(event) {
event.preventDefault();
try {
await axios.post("https://localhost:7195/api/Student/AddStudent", {
stname: stname,
course: course,
});
alert("Student Registation Successfully");
setId("");
setName("");
setCourse("");
Load();
} catch (err) {
alert(err);
}
}
async function editStudent(students) {
setName(students.stname);
setCourse(students.course);
setId(students.id);
}
async function DeleteStudent(id) {
await axios.delete("https://localhost:7195/api/Student/DeleteStudent/" + id);
alert("Employee deleted Successfully");
setId("");
setName("");
setCourse("");
Load();
}
async function update(event) {
event.preventDefault();
try {
await axios.patch("https://localhost:7195/api/Student/UpdateStudent/"+ students.find((u) => u.id === id).id || id,
{
id: id,
stname: stname,
course: course,
}
);
alert("Registation Updateddddd");
setId("");
setName("");
setCourse("");
Load();
} catch (err) {
alert(err);
}
}
From <https://www.tutussfunny.com/react-with-asp-net-core-web-api-full-stack-crud-application/?expand_article=1>
******************************\_\_\_\_******************************
To access the Restful API: npm i axios
To install bootstrap css: npm i bootstrap
OR add the below to index.html file
<linkrel="stylesheet"href="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css"integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm"crossorigin="anonymous">
Now import these libraries as well in StudentCrud.js
******************************\_\_\_\_******************************
import axios from "axios";
import { useEffect, useState } from "react";
From <https://www.tutussfunny.com/react-with-asp-net-core-web-api-full-stack-crud-application/?expand_article=1>
******************************\_\_\_\_******************************
Backend : https://localhost:7178/swagger/index.html
Frontend:
