users[icon:user,color:blue]{
  id string pk
  firstName string
  lastName string
  email string unique
  password string
  isVerified boolean
  isActive boolean
  role enum['doctor','patient']
  createdAt timestamp
  updatedAt timestamp
}

tokens[icon:key]{
  id string pk
  userId string fk
  token string
  tokenType enum['refreshToken','verificationToken','resetPasswordToken']
  expiresAt timestamp
  createdAt timestamp
  updatedAt timestamp
}

doctors_profile[icon:doctor,color:blue]{
  id string pk
  dob string
  gender enum['male','female','other']
  userId string fk unique
  specializationId string fk
  experienceInYears number
  createdAt timestamp
  updatedAt timestamp
}

patients_profile[icon:user,color:blue]{
  id string pk
  userId string fk unique
  dob string
  gender enum['male','female','other']
  address string
  createdAt timestamp
  updatedAt timestamp
}

departments[color:yellow]{
  id string pk
  name string
  description string
  createdAt timestamp
  updatedAt timestamp
}

specializations[color:yellow]{
  id string pk
  departmentId string fk
  name string
  description string
  createdAt timestamp
  updatedAt timestamp
}

appointments[color:purple]{
  id string pk
  patientId string fk
  doctorId string fk
  scheduledAt timestamp
  status enum['scheduled','completed','cancelled','no_show']
  createdAt timestamp
  updatedAt timestamp
}

consultation_visits[icon:book,color:purple]{
  id string pk
  appointmentId string fk unique
  createdAt timestamp
  updatedAt timestamp
}

diagnostic_tests[icon:test-tube,color:purple]{
  id string pk
  consultationId string fk
  name string
  description string
  status enum['prescribed','in_progress','completed']
  createdAt timestamp
  updatedAt timestamp
}

reports[icon:report, color:red]{
  id string pk
  diagnosticTestId string fk unique
  fileUrl string
  isGenerated boolean
  generatedAt timestamp
  createdAt timestamp
  updatedAt timestamp
}

payments[icon:money,color:green]{
  id string pk
  consultationId string fk unique
  amount decimal(10,2)
  paymentMethod enum['upi','card','cash']
  paymentStatus enum['pending','paid','failed','refunded']
  transactionId string
  paidAt timestamp
  createdAt timestamp
  updatedAt timestamp
}

tokens.userId <> users.id

doctors_profile.userId <> users.id
patients_profile.userId <> users.id

specializations.departmentId <> departments.id

appointments.patientId <> users.id
appointments.doctorId <> users.id

consultation_visits.appointmentId <> appointments.id

diagnostic_tests.consultationId  <> consultation_visits.id

reports.diagnosticTestId <> diagnostic_tests.id

payments.consultationId  <> consultation_visits.id