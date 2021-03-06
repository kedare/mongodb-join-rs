This small script allow a host to join a remove MongoDB RS.

It connects to the RS and run the correct command to integrate the new host into it.

It support hidden hosts and custom priority.

You first have to make sure that the new host has correct configuration (Authentication, keyfile, etc.)

Here is an example of run :

    PS C:\Users\mathieu.poussin\Desktop> mongo_join_rs --connection-string "mongodb://admin:admin@10.75.50.40,10.74.50.50,10.75.50.51/admin" --ssl --hostname 10.10.0.66 --priority 0.0 --hidden
    [2016-12-19 16:38:30.637167] INFO: JoinRs: Connecting to existing RS
    [2016-12-19 16:38:30.638168] INFO: JoinRs: Connected !
    [2016-12-19 16:38:30.638668] INFO: JoinRs: Determinating ID for the new host
    [2016-12-19 16:38:31.511956] INFO: JoinRs: Current RS configuration:
    {'_id': 'myRs',
     'members': [{'_id': 0,
                  'arbiterOnly': False,
                  'buildIndexes': True,
                  'hidden': False,
                  'host': 'gc-xxx-live-1:27017',
                  'priority': 1.0,
                  'slaveDelay': 0,
                  'tags': {},
                  'votes': 1},
                 {'_id': 1,
                  'arbiterOnly': False,
                  'buildIndexes': True,
                  'hidden': False,
                  'host': 'gc-xxx-live-2:27017',
                  'priority': 1.0,
                  'slaveDelay': 0,
                  'tags': {},
                  'votes': 1},
                 {'_id': 2,
                  'arbiterOnly': False,
                  'buildIndexes': True,
                  'hidden': False,
                  'host': 'gc-xxx-live-3:27017',
                  'priority': 1.0,
                  'slaveDelay': 0,
                  'tags': {},
                  'votes': 1},
                 {'_id': 3,
                  'arbiterOnly': False,
                  'buildIndexes': True,
                  'hidden': True,
                  'host': 'gc-lab-xxx-1:27017',
                  'priority': 0.0,
                  'slaveDelay': 0,
                  'tags': {},
                  'votes': 1}],
     'protocolVersion': 1,
     'settings': {'catchUpTimeoutMillis': 2000,
                  'chainingAllowed': True,
                  'electionTimeoutMillis': 10000,
                  'getLastErrorDefaults': {'w': 1, 'wtimeout': 0},
                  'getLastErrorModes': {},
                  'heartbeatIntervalMillis': 2000,
                  'heartbeatTimeoutSecs': 10,
                  'replicaSetId': ObjectId('xxx')},
     'version': 9}
    [2016-12-19 16:38:31.555702] INFO: JoinRs: Last ID is [3], Next ID will be [4]
    [2016-12-19 16:38:31.556565] INFO: JoinRs: Joining RS
    [2016-12-19 16:38:31.999751] INFO: JoinRs: Done!

I can also be used with "--leave" to leave the RS instead of joining it.
