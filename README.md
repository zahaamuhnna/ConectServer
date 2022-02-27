const  {MongoClient} = require('mongodb');

async function main(){
    const uri = "mongodb+srv://zahaa:za2211@cluster0.pwibb.mongodb.net/myFirstDatabase?retryWrites=true&w=majority";

    const client = new MongoClient(uri);
    try {
        await client.connect();
await listDataBases(client);
    }catch(e){
        console.error();
    }finally {
        await client.close();
    }
    }
main().catch(console.error);

async function listDataBases( client){
  const DataBasesList =  await client.db().admin().listDataBases();
  console.log("Databases:");
  DataBasesList.databases.forEach(db => {
      console.log('- ${db.name}')
  })
}
