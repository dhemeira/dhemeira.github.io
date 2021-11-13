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
    .then(function (arr) {
        for (int i=0; i < arr.length(); i++) {
            var response = arr.getJSONObject(i)
            console.log(response)
            var element = document.querySelector('#output').appendChild(document.createElement('table'))
            element = element.appendChild(document.createElement('thead'))
            element = element.appendChild(document.createElement('tr'))
            for (const [key, value] of Object.entries(response)) {
                console.log(key, value)
            }
            for (const key of Object.keys(response)) {
                let temp = element.appendChild(document.createElement('th'))
                temp.appendChild(document.createTextNode(`${key}`))
            }
            element = document.querySelector('table').appendChild(document.createElement('tbody'))
            element = element.appendChild(document.createElement('tr'))
            for (const value of Object.values(response)) {
                let temp = element.appendChild(document.createElement('td'))
                temp.appendChild(document.createTextNode(`${value}`))
            }
        }
    })
</script>
