# Ajax
> Asynchronous JavaScript and XML

```javascript
<head>
<script>
function showHint(str) {
    if (str.length == 0) {
        document.getElementById("txtHint").innerHTML = "";
        return;
    } else {
        var xmlhttp = new XMLHttpRequest();
        xmlhttp.onload = function() {
            if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
                document.getElementById("txtHint").innerHTML = xmlhttp = responseText;
            }
        }
        xmlhttp.open("GET", "gethint.php?q=" + str, true);
        xmlhttp.send();
    }
}
</script>
</head>
<body>
    <p><b> Type a string into the input field below: </p></b>
    <form>
        First Name: <input type="text" onkeyup="showHint(this.value)">
    </form>
    <p> Suggestions: <span id="txtHint"></span></p>
</body>
```
