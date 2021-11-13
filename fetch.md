---
title: Fetch
---

# Fetch

[Home](README.md) 
[About](about.md)

<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
<link type="text/css" rel="stylesheet" href="main.css" />
<div id="output"></div>
<script>
    let testPromise = fetch('https://forexlaravel.herokuapp.com/api/test', {
    method: 'GET',            
    })
    .then(function (response) {
        return response.json()
    })
    .then(function (arr) {
        let element = document.querySelector('#output').appendChild(document.createElement('table'))
        element.setAttribute("id", "fetch-table")
        element = element.appendChild(document.createElement('thead'))
        element = element.appendChild(document.createElement('tr'))
        for (let i = 0; i < arr.length; i++) { 
            let response = arr[i]
            console.log(response)
            if(i == 0) {
                for (const key of Object.keys(response)) {
                    let temp = element.appendChild(document.createElement('th'))
                    temp.appendChild(document.createTextNode(`${key}`))
                }
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
