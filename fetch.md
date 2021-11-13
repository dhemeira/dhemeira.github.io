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
        var element = document.querySelector('#output').appendChild(document.createElement('table'))
        element = element.appendChild(document.createElement('thead'))
        element = element.appendChild(document.createElement('tr'))
        for (const [key, value] of Object.entries(response)) {
            console.log(key, value)
        }
        for (const key of Object.keys(response)) {
            element = element.appendChild(document.createElement('th'))
            element.appendChild(document.createTextNode(`${key}`))
        }
        element = document.querySelector('table').appendChild(document.createElement('tbody'))
        element = element.appendChild(document.createElement('tr'))
        for (const value of Object.values(response)) {
            element = element.appendChild(document.createElement('td'))
            element.appendChild(document.createTextNode(`${value}`))
        }
    })
</script>
