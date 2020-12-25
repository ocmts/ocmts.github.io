## Object Cloud Mapper

Backend code is boring, why not automate it. OCM allows you to only focus on frontend logic. All you need to do is to define a couple of typescript classes, type a cli command to get a working application, including both frontend and backend. OCM will deploy services to the cloud and create database tables. Here is a quick example:

We use a typescript class (src/Catalog/Private/Product.ts) to represent a table

```ts
import * as Biz from '@ocmts/biz';

@Biz.published
export class Product extends Biz.ActiveRecord {
  public name: string;
  public price: number;
}
```

Define some initial products (src/init/Catalog/Private/Product.json)

```json
[
  { "name": "keybord A", "price": 100 },
  { "name": "mouse B", "price": 102 }
]
```

Then deploy them into the cloud:

```sh
ocm model update
```

In frontend code (src/Catalog/Ui/React/demo.tsx), we can query the products using:

```ts
import * as Biz from '@ocmts/biz';
import { Product } from '@/Catalog/Private/Product';

const scene = new Biz.Scene();
const products = await scene.query(Product, { name: 'mouse B' });
```
