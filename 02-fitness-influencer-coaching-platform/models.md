users [icon: user, color: blue] {
  id string pk
  firstName string
  lastName string
  email string
  password string
  isVerfied boolean
  isActive boolean
  role enum['client','trainer']
  createdAt timestamp
  updatedAt timestamp
}

tokens [icon:key]{
  id string pk
  userId string fk
  token string 
  tokentype enum['refreshToken','verificationToken','resetPasswordToken']
  expiresAt timestamp
  isUsed boolean
  createdAt tiomestamp
  updatedAt timestamp
}

trainer_clients(many to many)[icon:user-check, color:yellow]{
  id string pk
  trainerId string(userId trainer role) fk
  clientId string fk
  startedAt timestamp
  endedAt timestamp(nullable)
  createdAt tiomestamp
  updatedAt timestamp
}

plans [color:purple]{
  id string pk
  name string 
  description string
  price number
  durationInDays number
  createdBy string(userId trainer role) fk
  createdAt tiomestamp
  updatedAt timestamp
}

sessions[color:red]{
  id string pk
  clientId string fk
  trainerId string fk
  planId string fk (can be nullable)
  scheduledAt timestamp
  duration number
  type enum[consultation, live]
  status (scheduled, completed, cancelled)
  meetingLink string 
  createdAt tiomestamp
  updatedAt timestamp
}

subscriptions[color:red]{
  id string pk
  clientId string(userId trainer role) fk
  planId string fk
  trainerId string(userId trainer role) fk
  startDate timestamp
  endDate timestamp
  status enum[active, expired, cancelled]
  createdAt tiomestamp
  updatedAt timestamp
}

payments[icon:money, color:green]{
  id string pk
  planId string fk
  amount float(decimal upto 2 diigts)
  paymentMethod enum['cod','upi','card']
  paymentStatus enum['pending','paid','failed','refunded']
  transactionId string
  paidAt timestamp
  createdAt tiomestamp
  updatedAt timestamp
}

progressTracks[icon:progress, color:orange]{
 id string pk
 clientId string(userId user role) fk
 recordedBy string(user trainer role) fk
 metricType enum[heightInCm,weightInKgs,bmi,fat_percentage]
 trackDate timestamp
 value float(decimal upto 2 diigts)
 createdAt tiomestamp
 updatedAt timestamp
}

checkIns[color:black]{
  id string pk
  clientId string(useId user role) fk
  trainerId string(userId trainer role) fk
  date timestamp
  weight timestamp
  notes string
  createdAt timestamp
  updatedAt timestamp
}

tokens.userId <> users.id

trainer_clients(many to many).clientId <> users.id
trainer_clients(many to many).trainerId <> users.id

plans.createdBy <> users.id

sessions.clientId <> users.id
sessions.trinerId <> users.id
sessions.planId  <> subscriptions.id

subscriptions.clientId <> users.id
subscriptions.userId <> users.id
subscriptions.planId  <> plans.id

payments.planId <> subscriptions.id

progressTracks.clientId <> users.id
progressTracks.recordedBy <> users.id

checkIns.clientId <> users.id
checkIns.trainerId <> users.id