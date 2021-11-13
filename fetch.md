---
title: Home
layout: page
---
<div id="output"></div>
<script>
    let testPromise = fetch('https://forexlaravel.herokuapp.com/api/test', {
    method: 'GET',            
    })
    .then(function (response) {
        return response.json()
    })
    .then(function (response) {
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
        var textNode = document.createTextNode(output);
        document.querySelector('#output').appendChild( textNode );
    })
</script>
