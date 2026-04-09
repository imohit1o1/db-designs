vehicleCategories [icon:truck, color:blue] {
  id string pk
  name enum['bike','car','suv','ev','cab']
  description string
  createdAt timestamp
  updatedAt timestamp
}

vehicles [icon:car, color:blue] {
  id string pk
  vehicleNumber string unique
  vehicleCategoryId string fk
  ownerName string
  phone string
  createdAt timestamp
  updatedAt timestamp
}

parkingZones [icon:map, color:green] {
  id string pk
  name string
  description string
  createdAt timestamp
  updatedAt timestamp
}

parkingLevels [icon:layers, color:green] {
  id string pk
  zoneId string fk
  levelNumber int
  createdAt timestamp
  updatedAt timestamp
}

spotCategories [icon:tag, color:green] {
  id string pk
  name enum['general','vip','staff','exhibitor','cosplayer','ev_charging']
  description string
  createdAt timestamp
  updatedAt timestamp
}

parkingSpots [icon:parking, color:green] {
  id string pk
  levelId string fk
  spotNumber string
  spotCategoryId string fk
  vehicleCategoryId string fk
  isActive boolean
  createdAt timestamp
  updatedAt timestamp
}

parkingSessions [icon:clock, color:orange] {
  id string pk
  vehicleId string fk
  spotId string fk
  entryTime timestamp
  exitTime timestamp nullable
  status enum['active','completed','cancelled']
  createdAt timestamp
  updatedAt timestamp
}

tickets [icon:ticket, color:orange] {
  id string pk
  sessionId string fk
  ticketNumber string unique
  issuedAt timestamp
}

payments [icon:credit-card, color:red] {
  id string pk
  sessionId string fk
  amount decimal
  paymentMethod enum['cash','upi','card']
  paymentStatus enum['pending','paid','failed']
  paidAt timestamp nullable
  createdAt timestamp
}

pricingRules [icon:settings, color:purple] {
  id string pk
  vehicleCategoryId string fk
  spotCategoryId string fk
  pricePerHour decimal
  createdAt timestamp
}


vehicles.vehicleCategoryId <> vehicleCategories.id

parkingLevels.zoneId <> parkingZones.id

parkingSpots.levelId  <> parkingLevels.id
parkingSpots.spotCategoryId <> spotCategories.id
parkingSpots.vehicleCategoryId <> vehicleCategories.id

parkingSessions.vehicleId <> vehicles.id
parkingSessions.spotId <> parkingSpots.id

tickets.sessionId <> parkingSessions.id

payments.sessionId <> parkingSessions.id

pricingRules.vehicleCategoryId <> vehicleCategories.id
pricingRules.spotCategoryId <> spotCategories.id
