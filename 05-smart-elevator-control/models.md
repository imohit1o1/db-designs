buildings [icon: building, color: blue] {
  id string pk
  name string
  address string
  createdAt timestamp
  updatedAt timestamp
}

floors [icon: layers] {
  id string pk
  buildingId string fk
  floorNumber int
  label string
  createdAt timestamp
}

elevator_shafts [icon: grid] {
  id string pk
  buildingId string fk
  shaftNumber int
  createdAt timestamp
}

elevators [icon: activity, color: green] {
  id string pk
  buildingId string fk
  shaftId string fk
  code string
  capacity int
  installedAt timestamp
  createdAt timestamp
  updatedAt timestamp
}

elevator_floor_map [icon: link] {
  id string pk
  elevatorId string fk
  floorId string fk
}

floor_requests [icon: send, color: orange] {
  id string pk
  buildingId string fk
  sourceFloorId string fk
  destinationFloorId string fk
  direction enum['UP','DOWN']
  status enum['PENDING','ASSIGNED','COMPLETED','CANCELLED']
  requestedAt timestamp
}

ride_assignments [icon: target] {
  id string pk
  requestId string fk
  elevatorId string fk
  assignedAt timestamp
}

ride_logs [icon: activity] {
  id string pk
  elevatorId string fk
  requestId string fk
  startFloorId string fk
  endFloorId string fk
  startTime timestamp
  endTime timestamp
  duration int
}
ride_stops [icon: map] {
  id string pk
  rideLogId string fk
  floorId string fk
  stopOrder int
  arrivalTime timestamp
  departureTime timestamp
}
elevator_status_logs [icon: cpu, color: purple] {
  id string pk
  elevatorId string fk
  status enum['IDLE','MOVING','MAINTENANCE','OFFLINE']
  currentFloorId string fk
  recordedAt timestamp
}

maintenance_records [icon: tool] {
  id string pk
  elevatorId string fk
  type enum['INSPECTION','REPAIR','EMERGENCY']
  description string
  status enum['SCHEDULED','IN_PROGRESS','COMPLETED']
  startedAt timestamp
  completedAt timestamp
  createdAt timestamp
}


floors.buildingId <> buildings.id
elevator_shafts.buildingId <> buildings.id
elevators.buildingId <> buildings.id
elevator_groups.buildingId <> buildings.id
floor_requests.buildingId <> buildings.id

elevators.shaftId <> elevator_shafts.id

elevator_group_map.groupId <> elevator_groups.id
elevator_group_map.elevatorId <> elevators.id

elevator_floor_map.elevatorId <> elevators.id
elevator_floor_map.floorId <> floors.id

floor_requests.sourceFloorId <> floors.id
floor_requests.destinationFloorId <> floors.id

ride_assignments.requestId <> floor_requests.id
ride_assignments.elevatorId <> elevators.id

ride_logs.elevatorId <> elevators.id
ride_logs.requestId <> floor_requests.id
ride_logs.startFloorId <> floors.id
ride_logs.endFloorId <> floors.id

ride_stops.rideLogId <> ride_logs.id
ride_stops.floorId <> floors.id

elevator_status_logs.elevatorId <> elevators.id
elevator_status_logs.currentFloorId <> floors.id

maintenance_records.elevatorId <> elevators.id