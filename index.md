## Object Cloud Mapper

Backend code is boring, why not automate it. ocm allows you to focus on frontend logic. All you need to do is to define a couple of typescript classes, and type a cli command to get a working application, including frontend and backend. ocm will deploy the service to cloud and create the database tables. Here is a quick example:

```ts
import * as Biz from '@octms/biz';

// src/Catalog/Public/Product.ts
export class Product extends Biz.ActiveRecord {
  public name: string;
  public price: number;
}
```

after we defined the classes, we deploy them into the cloud:

```sh
ocm model update
```


