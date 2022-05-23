# Taller-De-Mongodb

const database = 'Empresa';
const collection = 'Empleado';

use(database);
1.
db.createCollection(collection);
2.
db.Empleado.insertOne(
	{'_id': 0, 'nombre': 'Edward', 'apellido': 'Ovalle', 'cargo': 'Ing Sistemas', 'salario': '2900000'}
	);
3.
db.Empleado.insertMany([
	{'_id': 1, 'nombre': 'Andres', 'apellido': 'Cepeda', 'cargo': 'Administrador de empresas', 'salario': '15000000'}, 
      {'_id': 2, 'nombre': 'Orfa', 'apellido': 'Arias', 'cargo': 'Ing Industrial', 'salario': '2000000'}
	]);
4.
db.Empresa.insertMany([
	{'nombre': 'Empresa A', 'Dirección': 'Carrera 30 14', 'telefono': 1234567890, 'fecha de creación': new Date('2022-03-02')},
      {'nombre': 'Empresa B', 'Dirección': 'Av primera de mayo 30', 'telefono': 7891245630, 'fecha de creación': new Date('2021-12-24')},
      {'nombre': 'Empresa C', 'Dirección': 'Calle 78 12', 'telefono': 8711234456, 'fecha de creación': new Date('2022-04-03')}]);
5.
db.Empleado.replaceOne({'_id': 0}, {'_id': 0, 'nombre': 'Carolina', 'apellido': 'Leon', 'cargo': 'Astronauta', 'salario': 3000000, 'Empresa_Id': ObjectId("628af94d9e08d2d6bc6789e9")})
db.Empleado.replaceOne({'_id': 1}, {'_id': 1, 'nombre': 'Cenaida', 'apellido': 'Anzola', 'cargo': 'Contador', 'salario': 2000000, 'Empresa_Id': ObjectId("628af94d9e08d2d6bc6789e9")})
db.Empleado.replaceOne({'_id': 2}, {'_id': 2, 'nombre': 'Saul', 'apellido': 'Ramirez', 'cargo': 'Ing mecanico', 'salario': 1500000, 'Empresa_Id': ObjectId("628af94d9e08d2d6bc6789e8")})
6.
db.Empresa.aggregate([
    {
        $match: {
            _id: ObjectId("628af94d9e08d2d6bc6789e9")
            }
    }
    ,{
        $lookup: {
            from: "Empleado",
            localField: "_id",
            foreignField: "Empresa_Id",
            as: "Empleado "
            }
    }
]);
7.
db.Empleado.deleteMany({"Empresa_Id": ObjectId("628af94d9e08d2d6bc6789e9")})
db.Empleado.find()
8.
db.Empresa.updateOne({'_id': ObjectId("628af94d9e08d2d6bc6789e8")}, {$set: {'nombre': 'Universidad Ean'}})
9.
db.Empleado.find({$and: [{'salario': {$gte: 1000000}}, {'salario': {$lte: 6000000}}]})
10.
db.Empleado.find({'_id': ObjectId("628af94d9e08d2d6bc6789e8")}, {"salario": 1})
