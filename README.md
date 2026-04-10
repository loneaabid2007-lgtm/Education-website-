<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EduSearch</title>

<style>
body{
font-family:Arial;
background:#f2f2f2;
margin:0;
}

header{
background:#1565c0;
color:white;
text-align:center;
padding:25px;
}

.search-box{
text-align:center;
margin:30px;
}

input{
width:60%;
padding:12px;
font-size:18px;
border-radius:6px;
border:1px solid #ccc;
}

button{
padding:12px 20px;
font-size:16px;
background:#1565c0;
color:white;
border:none;
border-radius:6px;
cursor:pointer;
}

#results{
max-width:900px;
margin:auto;
padding:20px;
}

.result{
background:white;
padding:15px;
margin-bottom:15px;
border-radius:8px;
box-shadow:0 2px 5px rgba(0,0,0,0.1);
}

a{
text-decoration:none;
color:#1565c0;
font-size:20px;
}

p{
font-size:14px;
}
</style>
</head>

<body>

<header>
<h1>EduSearch</h1>
<p>Search Any Educational Topic</p>
</header>

<div class="search-box">
<input type="text" id="searchInput" placeholder="Search education topic...">
<button onclick="searchWiki()">Search</button>
</div>

<div id="results"></div>

<script>

async function searchWiki(){

let query=document.getElementById("searchInput").value;

let url=`https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=${query}&format=json&origin=*`;

let response=await fetch(url);

let data=await response.json();

let results=document.getElementById("results");

results.innerHTML="";

data.query.search.forEach(item => {

results.innerHTML += `
<div class="result">
<a href="https://en.wikipedia.org/wiki/${item.title}" target="_blank">${item.title}</a>
<p>${item.snippet}...</p>
</div>
`;

});

}

</script>

</body>
</html>
