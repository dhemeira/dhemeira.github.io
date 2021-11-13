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
        var node = document.createElement(table)
        var element = document.querySelector('#output').appendChild(node)
    
        node = document.createElement(thead)
        element = element.appendChild(node)
    
        node = document.createElement(tr)
        element = element.appendChild(node)
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
        var textNode = document.createTextNode(output)
        document.querySelector('#output').appendChild( textNode )
    })
</script>
