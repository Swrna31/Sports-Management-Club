
# Assignment-3

- _Date Created_: 15 JUL 2022
- _Last Modification Date_: 15 JUL 2022
- _Heroku URL Frontend_: <https://sportify-prd.herokuapp.com/>
- _Heroku URL Backend_: <https://sportify-backend-prd.herokuapp.com/>

## Group Repo URLs

- _Gitlab URL Front-End_: <https://git.cs.dal.ca/ajayanthi/5709-group10>
- _Gitlab URL Back-End_: <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/tree/main>


## Individual Branch URLs

- _Gitlab URL Front-End_: <https://git.cs.dal.ca/ajayanthi/5709-group10/-/tree/alagu_swrnam_karruppiah>
- _Gitlab URL Back-End_: <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/tree/alaguswrnam_karruppiah>

## Authors

- [Alagu Swrnam Karruppiah](al581093@dal.ca) - _Maintener_

### Prerequisites

To have a local copy of this tutorial up and running on your local machine, you will first need to install the following libraries

```
Node.js
```

### Installing

In the project directory, you can run:

```
npm i
npm start
```

## Deployment

The code is deployed on heroku


## Built With

- [React](https://reactjs.org/docs/getting-started.html) - The web framework used
- [Node.js](https://nodejs.org/dist/latest-v16.x/docs/api/) - The web framework used
- [Mongoose](https://mongoosejs.com/) - The Mongoose library is used to connect with MongoDB which is the database for our application. It also provides ORM capabilities to conver the results into JSON with appropriate properties.
- [uuid](https://www.npmjs.com/package/uuid) - This library is used to generate UUID values for the different models used in the project.


## Features Implemented

- Payment Feature
- Merchandise Feature

## Files Implemented

### Front-End Files

- Integrated with _Prachi_ to send values to the payment. <https://git.cs.dal.ca/ajayanthi/5709-group10/-/blob/alagu_swrnam_karruppiah/src/pages/Membership/checkout.js>

- Integrated with _Prachi_ after successful payment. And displayed the membership details on the page. <https://git.cs.dal.ca/ajayanthi/5709-group10/-/blob/alagu_swrnam_karruppiah/src/pages/Membership/purchasedMembership.js>

- Primary Feature - <https://git.cs.dal.ca/ajayanthi/5709-group10/-/tree/alagu_swrnam_karruppiah/src/pages/Payment>

- Secondary Feature - <https://git.cs.dal.ca/ajayanthi/5709-group10/-/tree/alagu_swrnam_karruppiah/src/pages/Merchandise>


### Back-End Files

#### Controllers

- Primary Feature - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/controllers/stripe.js>

- Secondary Feature - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/controllers/merchandise.js>

- Integrated with _Prachi_ to get the payment details on success and store in the membership collection - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/controllers/membership.js>

#### Models

- Primary Feature - Integrated with the [STRIPE PAYMENT GATEWAY](https://stripe.com/docs/payments)

- Secondary Feature - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/models/merchandise.js>

- Trying to implement an additional feature if time permits - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/models/orders.js>


#### Routes

- Primary Feature - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/routes/stripe.js>

- Secondary Feature - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/routes/merchandise.js>



## Sources Used

### FrontEnd 

### File Name - <https://git.cs.dal.ca/ajayanthi/5709-group10/-/blob/alagu_swrnam_karruppiah/src/pages/Membership/purchasedMembership.js>

_Lines 61-64_

```
    axios.post(domain + '/api/membership/create-purchase', {
        backendReqBody,
        userId
      })
```

The code above was created by adapting the code in [AXIOS API](https://axios-http.com/docs/api_intro) as shown below:

```
axios.post(url[, data[, config]])
```

- The code in [AXIOS API](https://axios-http.com/docs/api_intro) was implemented
- [AXIOS API](https://axios-http.com/docs/api_intro)'s Code was used to connect to backend
- [AXIOS API](https://axios-http.com/docs/api_intro)'s Code was modified to connect to backend repo for the access of the database.

### File Name - <https://git.cs.dal.ca/ajayanthi/5709-group10/-/blob/alagu_swrnam_karruppiah/src/pages/Membership/checkout.js>

_Lines 78-94_

```
localStorage.setItem('backendReqBody', JSON.stringify(backendReqBody))
        axios({
          method: method,
          url: url,
          data: reqBody
        }).then(res => {
          axios.post(domain + '/api/stripe/create-checkout-session', {
            backendReqBody,
            userId
          }).then((response) => {
            if (response.data.url) {
              window.location.href = response.data.url
            }
          }).catch((error) => console.log(error.message))
        }).catch(err => {
          console.log(err);
        })


```

The code above was created by adapting the code in [Freedcodecamp](https://www.freecodecamp.org/news/how-to-use-localstorage-with-react-hooks-to-set-and-get-items/) as shown below:

```
localStorage.setItem('items', JSON.stringify(items));
const items = JSON.parse(localStorage.getItem('items'));
  if (items) {
   setItems(items);
  }
```

- The code in [Freedcodecamp ](https://www.freecodecamp.org/news/how-to-use-localstorage-with-react-hooks-to-set-and-get-items/)was implemented
- [Freedcodecamp](https://www.freecodecamp.org/news/how-to-use-localstorage-with-react-hooks-to-set-and-get-items/)'s Code was used to get existence of an element in the localStorage
- [Freedcodecamp](https://www.freecodecamp.org/news/how-to-use-localstorage-with-react-hooks-to-set-and-get-items/)'s Code was modified by the app requirements I created.


### BackEnd 

### File Name - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/models/merchandise.js>

_Lines 3-14_

```
    var ObjectIdSchema = Schema.ObjectId;
var ObjectId = mongoose.Types.ObjectId;

const merchandiseSchema = new Schema({

    product_name: String,
    product_price: Number,
    product_description: String,
    product_image: String,
    product_id: {type:ObjectIdSchema, default: function () { return new ObjectId()} }
    }, 
{ _id : false })


```

The code above was created by adapting the code in [Mongoose's Documentation ](https://mongoosejs.com/docs/schematypes.html#objectids) as shown below:

```
const mongoose = require('mongoose');
const carSchema = new mongoose.Schema({ driver: mongoose.ObjectId });
const Car = mongoose.model('Car', carSchema);

const car = new Car();
car.driver = new mongoose.Types.ObjectId();

typeof car.driver; // 'object'
car.driver instanceof mongoose.Types.ObjectId; // true

car.driver.toString(); // Something like "5e1a0651741b255ddda996c4"
```

- The code in [Mongoose's Documentation](https://mongoosejs.com/docs/schematypes.html#objectids) was implemented
- [Mongoose's Documentation](https://mongoosejs.com/docs/schematypes.html#objectids)'s Code was used to get objectID
- [Mongoose's Documentation](https://mongoosejs.com/docs/schematypes.html#objectids)'s Code was modified by the app requirement

### File Name - <https://git.cs.dal.ca/kabtiyal/5709-g10-sportify-backend/-/blob/main/controllers/stripe.js>
_Lines 8-31_

```
const checkoutSession = async (request,response) => {
    const line_items = request.body.backendReqBody.map((item)=>{
        return{
            price_data: {
                currency: 'CAD',
                product_data: {
                    name: item.plan_name,
                },
                unit_amount: item.total_cost * 100,
              },
              quantity: 1,
        }
    })
    console.log(line_items)
    const session = await stripe.checkout.sessions.create({
        line_items,
        mode: 'payment',
        success_url: 'http://localhost:3000/purchased-membership?payment=success',
        cancel_url: 'http://localhost:3000/membership',
      });
    
      response.send({url: session.url});
    
}


```

The code above was created by adapting the code in [STRIPE DOCS](https://stripe.com/docs/payments/checkout/how-checkout-works) as shown below:


```

const stripe = require('stripe')('sk_test_51LAz4KC9WWOmeUQqrPNjR1MoMg8QUwat6VjKu7criZO85933G7zghbRiOZl4u6L8aY4VetIlnUEkxANmg24K018D000U1euugz');
const express = require('express');
const app = express();
app.use(express.static('public'));

const YOUR_DOMAIN = 'http://localhost:4242';

app.post('/create-checkout-session', async (req, res) => {
  const session = await stripe.checkout.sessions.create({
    line_items: [
      {
        // Provide the exact Price ID (for example, pr_1234) of the product you want to sell
        price: '{{PRICE_ID}}',
        quantity: 1,
      },
    ],
    mode: 'payment',
    success_url: `${YOUR_DOMAIN}/success.html`,
    cancel_url: `${YOUR_DOMAIN}/cancel.html`,
  });

  res.redirect(303, session.url);
});

app.listen(4242, () => console.log('Running on port 4242'));

```

- The code in [STRIPE DOCS ](https://stripe.com/docs/payments/checkout/how-checkout-works)was implemented
- [STRIPE DOCS](https://stripe.com/docs/payments/checkout/how-checkout-works)'s Code was used to get stripe payment
- [STRIPE DOCS](https://stripe.com/docs/payments/checkout/how-checkout-works)'s Code was modified by the app requirements I created.

