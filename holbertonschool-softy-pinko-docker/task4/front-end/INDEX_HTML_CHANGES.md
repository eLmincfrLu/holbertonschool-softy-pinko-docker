# index.html-a elave etmeli olduğun deyisiklikler (task3)

`softy-pinko-front-end/index.html` faylini asagidaki kimi redakte et:

## 1) Yeni `<h1 id="dynamic-content">` elave et (mövcud başlıqdan əvvəl)

```html
<div class="offset-xl-3 col-xl-6 offset-lg-2 col-lg-8 col-md-12 col-sm-12">
    <h1 id="dynamic-content"></h1>
    <h1>We provide the best <strong>strategy</strong><br>to grow up your<strong>business</strong></h1>
    <a href="#features" class="main-button-slider">Discover More</a>
</div>
```

## 2) `</body>`-dən əvvəl bu script-i elave et

```html
<script>
    // Load dynamic data from the back-end on port 5252
    $(function() {
        $.ajax({
            type: "GET",
            url: "http://localhost:5252/api/hello",
            success: function(data) {
                console.log(data);
                $('#dynamic-content').text(data);
            }
        });
    });
</script>
```
