<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Document</title>
</head>

<body>
    <div id="output"></div>
    <script>
        let testPromise = fetch('https://forexlaravel.herokuapp.com/api/test', {
            method: 'GET',            
        })
            .then(function (response) {
                return response.json()
            })
            .then(function (response) {
                let outputtest = '<p>asd</p>'
                document.querySelector('#output').innerHtml = outputtest
                console.log(response)
                let output = '<table><thead><tr>'
                for (const [key, value] of Object.entries(response)) {
                    console.log(key, value)
                }
                for (const key of Object.keys(response)) {
                    output += `<th>${key}</th>`
                }
                output += '</tr></thead><tbody><tr>'
                for (const value of Object.values(response)) {
                    output += `<td>${value}</td>`
                }
                output += '</tr></tbody></table>'
                document.querySelector('body').innerHtml = output
            })
    </script>
</body>

</html>
