# first<html>
<head>
<title>Androino</title>

<style>
body {
    background: #32323D;
}
div#content {
    padding-top:100px;
    width:150px;
    margin:auto;
}
div#output {
    border:1px solid black;
    background:white;
    text-align:center;
}
</style>

<script>
var droid = new Android();
var fetch_data = function() {
    // fire the event that the python script is waiting for.
    droid.eventPost('fetch_data', '');
}
// this function gets called from the python script when it receives new sensor data.
droid.registerCallback('display_data', function(data) {
    document.getElementById('output').innerHTML = 'Sensor value: ' + data.data;
});
</script>

</head>

<body>
<div id="content">
    <div id="output">-</div>
    <button onclick="fetch_data();">get sensor data</button>
</div>
</body>
</html>
