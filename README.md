# MongoDb Örnekleri
#### Yazar: Mustafa Türköz
#### Web site: mustafaturkoz.blogspot.com

- Nodejs platformunda mongodb ve mongoose kullanılarak mongodb sorguları örneklendirilmiştir.
- Komutları deneyebilmek için öncelikle;
    - Nodejs,
    - Mongodb ve
    - Mongoose teknolojilerini yüklemeniz gerekir.
- Veritabanındaki verilerinizi ücretsiz bir uygulama olan Robo3T ile görüntüleyebilirsiniz.

## Connection (veritabanına nasıl bağlanırız?)
- Npm'den mongoose yüklenir.
- Bağlantı için opts parametresi ayarlanır.
- İsteğe bağlı olarak kullanıcı parolası ayarlanarak da giriş yapılabilir.
- `localhost:27017/mydb` bizim bağlantı adresimiz ve mydb yerine bağlanacağımız veritabanımızın adını yazıyoruz. 27017 ise mongodb'nin default portudur.
- Bağlantı başarılıysa Database connected! yazısını terminal ekranımızda göreceğiz.
```javascript
const mongoose = require('mongoose')

const opts = {
    promiseLibrary: require('bluebird'),
    useNewUrlParser: true,
    useCreateIndex: true,
    useUnifiedTopology: true,
    useFindAndModify: false,
    reconnectTries: Number.MAX_VALUE,
    autoReconnect: true
    /*
    auth: {
      user: 'mustafa',
      password: '123456',
    }
    */
}

mongoose.connect("localhost:27017/mydb", opts, function (err, client) {
    if (err) {
        console.log('Error occurred while connecting to MongoDB...\n', err);
    }
    console.log('Connected...');
})

mongoose.connection.on('connected', () => {
    console.log('Database connected!')
})
```

## Create (bir collection oluşturmak)
- Örnek bir user modeli oluşturmanız gerekir, biz burada hazır bir user modeli kullanarak işlemi gerçekledik.
- User(kullanıcı) bilgileri girilir ve save fonksiyonu ile kayıt işlemi gerçekleştirilir.
- Collection kelimesi sql'de tablo kelimesine eş gelir.
```javascript
const User = require('./models/user')
// ...
const newUser = new User({
    name: name,
    surname: surname,
    email: email,
    password: password
})

newUser.save((err) => {
    if (err) {
        console.log('error')
    } else {
        console.log('success')
    }
})
// ...
```

## Find (listeleme işlemleri)
continue..

