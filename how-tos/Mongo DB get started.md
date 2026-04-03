#mongo

Send a ping to confirm a successful connection
try:
    client.admin.command('ping')
    print("Pinged your deployment. You successfully connected to MongoDB!")
except Exception as e:
    print(e)


connect uri:
mongodb+srv://nluttenberger:[[Ii5K!dQ%40F3txZ3D7@methods26-cluster.f7nz9hl.mongodb.net]]/?appName=methods26-cluster

cluster:
methods_26

