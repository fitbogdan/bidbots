
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


# Protocol:

## Connection process:

Each client sends a connect request to the server.

The server accepts and it spanws a new thread.


In the thread: Check the hello message:

Each client sends their own HELLO message:

``` HELLO <type = ROBOT|VISUAL|ORDER> ```

Call the correct function according to the type.

If this client is type ORDER, and its the first of it's kind, then spawn a organiser thread.

(Only one organiser thread will be needed)


## Work based on client type:

### Order Client:

PLACE <product_name>

The order thread then does a query to look up the coords of that product name. It takes them and appends them to a list of coords, which it then adds to the shared state buffer, triggering an auction event (Which will be handled by the Organiser Thread)

When the order is done, it will send success.

TODO: The mechanism for how it will find out if its done.




