
BidBots:
A system for coordonating robot workers in a warehouse.

The Goal of this project is to create an efficient and robust auction based system for the retreival of products from the warehouse.

It will consist of 4 types of clients:
Client type 1 - The server, this one will cordonate the work of all the robots. It sends the job for auction with the workers, and picks the best offer.
            It will also have to handle cases where a robot dies during its job, so it can re asign that job to another robot.

Client type 2 - The robot worker. Will await for the auction from the server, and will bid until the auction is over or until it will recieve the job.
                If it gets the job, it will go ahead and do it.
                Robots will send hearbeat signals to the server periodically, to maintain contact and to be able to re asign the job in case it was lost.

Client type 3 - The client which sends the work to the server.

Client type 4 - The client which visualises graphically the robots at work.