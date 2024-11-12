# codetribe-mongodb

use Codetribe

db.createCollection("Facilitators")
db.Facilitators.insertOne({
    Name: "John Doe",
    Location: "Polokwane",
    Course: "Full-Stack Development"
})

db.createCollection("Trainees")
db.Trainees.insertOne({
    Name: "Jane Smith",
    Location: "Polokwane",
    Facilitator: "John Doe"
})

db.createCollection("Projects")
db.Projects.insertOne({
    Name: "Weather App",
    Course: "Full-Stack Development",
    Lesson: "API Integration"
})

db.Facilitators.find()
db.Trainees.find()
db.Projects.find()
