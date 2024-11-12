# codetribe-mongodb

use Codetribe

db.createCollection("Facilitators")
db.Facilitators.insertOne({
    Name: "Refilwe",
    Location: "Polokwane",
    Course: "Full-Stack Development"
})

db.createCollection("Trainees")
db.Trainees.insertOne({
    Name: "Frankie mosehla",
    Location: "Polokwane",
    Facilitator: "Refilwe"
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
