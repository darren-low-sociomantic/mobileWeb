# mobileWeb

This simple example of mobile web shows how to integrate the appkit for a non-native app, yet keep the original JS tracking codes for mobile campaigns.

If you are going to pull this project for local test, please remember to define the server location and token in js/config.js

Example:

```
server = "eu-sonar";
token = "12345-eu";
```

#### Example of using JavascriptInterface methods on homepage

```
<script type="text/javascript">

	/* If mobile web is opened by APP, trigger the JSinterface, otherwise trigger the normal JS tracking codes
	Please do not wrap our codes into wthe indow.onload or document ready (jquery) function */

	if (typeof android != "undefined") {

		android.reportSociomanticView();

	} else {

		// remember to change your server location and token ID
	    (function(){
	        var s   = document.createElement('script');
	        var x   = document.getElementsByTagName('script')[0];
	        s.type  = 'text/javascript';
	        s.async = true;
	        s.src   = ('https:'==document.location.protocol?'https://':'http://')
	                + '{server location}.sociomantic.com/js/2010-07-01/adpan/{your token ID}';
	        x.parentNode.insertBefore( s, x );
	    })();
	}

</script>
```

#### Example of using JavascriptInterface methods on category page

```
<script type="text/javascript">

	/* If mobile web is opened by APP, trigger the JSinterface, otherwise trigger the normal JS tracking codes
	Please do not wrap our codes into wthe indow.onload or document ready (jquery) function */

	// Define the full category path here
	var categoryPath = [ "Main category", "Sub category 1", "Sub category 2" ];

	if (typeof android != "undefined") {

		var categories = categoryPath;
		var categoryList = categories.toString(); // Convert the array to string for JSinterface readibility
		android.reportSociomanticCategoryView(categoryList);

	} else {

	    var product = {
	        category: categoryPath
	    };

	    // remember to change your server location and token ID
	    (function(){
	        var s   = document.createElement('script');
	        var x   = document.getElementsByTagName('script')[0];
	        s.type  = 'text/javascript';
	        s.async = true;
	        s.src   = ('https:'==document.location.protocol?'https://':'http://')
	                + '{server location}.sociomantic.com/js/2010-07-01/adpan/{your token ID}';
	        x.parentNode.insertBefore( s, x );
	    })();

	}

</script>
```

#### Example of using JavascriptInterface methods on product page

```
<script type="text/javascript">

	/* If mobile web is opened by APP, trigger the JSinterface, otherwise trigger the normal JS tracking codes
	Please do not wrap our codes into wthe indow.onload or document ready (jquery) function */

    var product = {
        identifier: 'SN123000',
        category: [ "Main category", "Sub category 1", "Sub category 2" ],
        fn: 'Product 1',
        description: 'I am product 1',
        brand: 'ABC',
        price: 100.00,
        amount: 130.00,
        currency: 'USD',
        url: 'http://wwww.test.com',
        photo: 'http://wwww.test.com/12345.png',
        valid: '0'
    };

	if (typeof android != "undefined") {

		var product = JSON.stringify(product); // Convert the object to string for JSinterface readibility
		android.reportSociomanticProductView(product);

	} else {

	    // remember to change your server location and token ID
	    (function(){
	        var s   = document.createElement('script');
	        var x   = document.getElementsByTagName('script')[0];
	        s.type  = 'text/javascript';
	        s.async = true;
	        s.src   = ('https:'==document.location.protocol?'https://':'http://')
	                + '{server location}.sociomantic.com/js/2010-07-01/adpan/{your token ID}';
	        x.parentNode.insertBefore( s, x );
	    })();

	}

</script>
```

#### Example of using JavascriptInterface methods on basket page

```
<script type="text/javascript">

	/* If mobile web is opened by APP, trigger the JSinterface, otherwise trigger the normal JS tracking codes
	Please do not wrap our codes into wthe indow.onload or document ready (jquery) function */

    var basket = {
        products: [
            { identifier: 'SN123000', amount: 100.00, currency: 'USD', quantity: 2 },
            { identifier: 'SN123888', amount: 120.00, currency: 'USD', quantity: 1 }
        ]
    };

	if (typeof android != "undefined") {

		var basketStr = JSON.stringify(basket); // Convert the object to string for JSinterface readibility
		android.reportSociomanticBasketView(basketStr);

	} else {

	    // remember to change your server location and token ID
	    (function(){
	        var s   = document.createElement('script');
	        var x   = document.getElementsByTagName('script')[0];
	        s.type  = 'text/javascript';
	        s.async = true;
	        s.src   = ('https:'==document.location.protocol?'https://':'http://')
	                + '{server location}.sociomantic.com/js/2010-07-01/adpan/{your token ID}';
	        x.parentNode.insertBefore( s, x );
	    })();

	}

</script>
```

#### Example of using JavascriptInterface methods on confirmation page

```
<script type="text/javascript">

	/* If mobile web is opened by APP, trigger the JSinterface, otherwise trigger the normal JS tracking codes
	Please do not wrap our codes into wthe indow.onload or document ready (jquery) function */

    var basket = {
        products: [
            { identifier: 'SN123000', amount: 100.00, currency: 'USD', quantity: 2 },
            { identifier: 'SN123888', amount: 120.00, currency: 'USD', quantity: 1 }
        ],
        transaction : 'TRANS12345',
        amount: 220.00,
        currency: 'USD'
    };

	if (typeof android != "undefined") {

		var basketStr = JSON.stringify(basket); // Convert the object to string for JSinterface readibility
		android.reportSociomanticTransactionView(basketStr);

	} else {

	    // remember to change your server location and token ID
	    (function(){
	        var s   = document.createElement('script');
	        var x   = document.getElementsByTagName('script')[0];
	        s.type  = 'text/javascript';
	        s.async = true;
	        s.src   = ('https:'==document.location.protocol?'https://':'http://')
	                + '{server location}.sociomantic.com/js/2010-07-01/adpan/{your token ID}';
	        x.parentNode.insertBefore( s, x );
	    })();

	}

</script>
```


