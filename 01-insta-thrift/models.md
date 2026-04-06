users [icon: user, color: blue] {
  id string pk
  firstName string
  lastName string
  email string
  password string
  isVerfied boolean
  isActive boolean
  createdAt timestamp
  updatedAt timestamp
}
tokens []{
  id string pk
  userId string fk
  token string 
  tokentype enum['refreshToken','verificationToken','resetPasswordToken']
  expiresAt timestamp
  isUsed boolean
  createdAt tiomestamp
  updatedAt timestamp
}

addresses[icon:map-pin]{
  id string pk
  userId string fk
  firstName string 
  lastName string
  countryCode string
  phone string
  city string
  area string
  pincode string
  createdAt tiomestamp
  updatedAt timestamp
}

categories[color:orange]{
  id string pk
  slug string
  name string
  description string(optional)
  createdAt tiomestamp
  updatedAt timestamp
}
products[icon:box , color:purple]{
  id string pk
  categoryId string fk
  slug string
  name string
  description string
  createdAt tiomestamp
  updatedAt timestamp
}
productVariant[icon:boxes, color:purple]{
  id string pk
  productId string fk
  sku string(optional)
  color string(optional)
  size enum[](optional)
  price float(decimal upto 2 digits)
}
inventory[]{
  id string pk
  productVariantId string fk
  isUnique boolean
  quantity number
  condition string(optional)
}
orders[icon:shopping-cart, color:green]{
  id string pk
  userId string fk
  orderNumber string
  orderStatus enum['created','confirmed','cancelled','completed']
  orderedAt timestamp
  createdAt tiomestamp
  updatedAt timestamp
}
orderItems[color:green]{
  id string pk
  orderId string fk
  productVariantId string fk
  quantity number
  orderPrice float(decimal upto 2 diigts)
}

shippings[icon:car,color:yellow]{
  id string pk
  userId string fk
  orderId string fk
  shipppingStatus enum['processing','shipped','not_shipped',out_for_delievery','delievred','returned']
  firstName string 
  lastName string
  countryCode string
  phone string
  city string
  area string
  pincode string
  shippedAt timestamp
  createdAt tiomestamp
  updatedAt timestamp
}
payments[icon:money, color:red]{
  id string pk
  orderId string fk
  paymentMethod enum['cod','upi','card']
  paymentStatus enum['pending','paid','failed','refunded']
  transactionId string
  paidAt timestamp
  createdAt tiomestamp
  updatedAt timestamp
}


tokens.userId  <> users.id
addresses.userId <> users.id
products.categoryId <> categories.id
productVariant.productId <> products.id
inventory.productVariantId <> productVariant.id
orders.userId <> users.id
orderItems.orderId <> orders.id
orderItems.productVariantId  <> productVariant.id
shippings.orderId <> orders.id
shippings.userId <> users.id
payments.orderId <> orders.id