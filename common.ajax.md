## Jquery multiple Ajax request with same data

```
function call_ajax(options){
    options.data = {id: 1, name: 'Fauji'};
    $.ajax(options);
}


call_ajax({
    url: 'http://localhost/first_request',
    success: function(response){
        console.log(response)
    }
});


call_ajax({
    url: 'http://localhost/first_request',
    method: 'POST',
    dataType: 'json',
    success: function(response){
        console.log(response)
    }
});

call_ajax({
    url: 'http://localhost/first_request',
    beforeSend: function(){
        $('#loading').show();
    },
    method: 'POST',
    dataType: 'json',
    success: function(response){
        console.log(response)
    }
});

call_ajax({
    url: 'http://localhost/first_request',
    beforeSend: function(){
        $('#loading').show();
    },
    method: 'POST',
    dataType: 'json',
    success: function(response){
        console.log(response)
    }, error: function(response){
    conosle.error(response);
    }, complete: function(response){
    $('#loading').hide();
    }
});


```