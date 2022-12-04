'''
Vishrutha Gopa
'''

# IMPORTANT: DO NOT CLOSE THE MAP WHILE PLAYING THE TEXT ADVENTURE

# Import pygame and sys
import pygame
from sys import exit


def display_map():
    """
    Blit the map onto a pygame window
    
    Params: 
        N/A
    Return: 
        N/A
    
    """

    # Load the Map
    map  = pygame.image.load("Layout_map.png")
    
    # Get the dimensions of the map
    (width,height) = map.get_size()

    # Create the screen
    screen = pygame.display.set_mode((width,height))
    pygame.display.set_caption('Map')

    #Blit and update the screen
    screen.blit(map,(0,0))
    pygame.display.update()


def display_instructions():
    """
    Display the instructions
    
    Params: 
        N/A
    Return: 
        N/A
    
    """
    print("\nIMPORTANT: PLEASE KEEP THE MAP OPEN WHILE PLAYING THE TEXT ADVENTURE. DO NOT CLOSE IT!")
    print("\nWelcome to the house! You can explore the house by typing the direction you would like to travel to.")
    print('''
    You may also choose any other following commands:
        TAKE: Pickup an item in the room you are in if there is any
        INVENTORY: Display the items in your inventory
        QUIT: Exit the game

    ''')    
    input("Press any key to begin the adventure: ")

def get_direction(nav, index,items, inventory, current_roomNumber):
    """
    Get the valid directions or commands from user
    
    Params: 
        nav, index,items, inventory, current_roomNumber
    Return: 
        choice  -- the valid direction the user would like to move in
    
    """

    while True:
        #Ask user for thier input
        choice = (input("\nType the direction you would like to go, or enter any of the commands (TAKE, INVENTORY, QUIT): ")).lower()

        # If user's input is a valid direction
        if choice in nav[index]:
            return choice
        
        # If the user decides to QUIT
        elif choice == "quit":
            print("GAME ENDED")
            pygame.quit()
            quit()
        
        # If user decides to take an item
        elif choice == "take":
            take_option(items, inventory, current_roomNumber)
        
        # If user decides to view their inventory
        elif choice == "inventory":
            inventory_option(items, inventory)
        
        # If user input is Invalid
        else:
            print("Invalid. Couldn't go in that direction or understand the command. Try again")

def take_option(items, inventory, current_roomNumber):
    """
    Take items from the current room a user is in (if any)
    
    Params: 
        items, inventory, current_roomNumber
    Return: 
        N/A
    
    """

    # Checks if there are any items in the room
    # If yes, add the item to inventory list and remove it from the item list
    if len(items[current_roomNumber]) > 0:
        print(f"You found {items[current_roomNumber][0]}!! How exciting!")
        
        inventory.append(items[current_roomNumber][0])
        items[current_roomNumber].pop(0)

    else:
        print("There is nothing to take :( ")


def inventory_option(items, inventory):
    """
    Display items in inventory
    
    Params: 
        items, inventory
    Return: 
        N/A
    
    """

    # Prints out the items in the inventory list
    if len(inventory) > 0:
        print("Here is your inventory:")

        for i in ((inventory)):
            print("\t",i)
    else:
        print("Your inventory is empty.")


def main():
    """
    Main function

    Params: 
        N/A
    Return: 
        N/A
    """

    # List of all the rooms in the house
    rooms = ["Porch", "Foyer", "Closet", "Hallway", "Office", 
             "Dining Room", "Theatre", "Walkway","Pantry","Mudroom",
             "Garage", "Driveway", "Kitchen", "Living Room", "Bedroom", 
             "Walk-in Closet", "Laundry", "Bathroom", "Backyard", "Shed", 
             "Garden"
    ]
    
    # List of room's descriptions
    room_descriptions = ["What a beautuful view outside! Love the bushes surrounding the house.", "Hang up your coat. Don't leave it on the chair.", "You have a lot of stuff here! Sooner or later, the door won't be able to close as easily.", "What a long hallway... Looks a bit sketchy.", "Oh look at how organized this room is. You need to finish stapling your papers.",
    "The chandelier hanging above the table really catches the eye. Cannot wait for dinner!!", "Woah look at those comfy seats... Would probably be able to fall asleep on them in moments", "Um, this walkway is a bit tight. It's getting cramped in here.", "Yum, look at all those snacks. Grab one if you are hungry.", "Its so dark in here. The lightbulb isn't working. Should light a candle",  
    "Oh looks like you forgot to lock you car. The car's alarm went off, its so loud in here.", "Brrr...So cold out here... Look at the birds migrating south.", "Lots of natural light in here... It makes the color of the cabinets pop out.", "It is getting chilly in here, looks like the heater broke.", "Woah this is so spacious! It feels so empty in here, should probably buy some more furniture later today.", 
    "Wowm this closet is full. Its like a jungle in there.", "Look at those clothes piling up in the laundry basket...Should do them this weekend.", "Oh no, ran out of shampoo. There should be some in the cabinet below the sink.", "Oh my, the leaves are already falling of the tree. I can't belive its already fall.", "So many tools in here. The grass seems a bit too long, its probably time to cut it. Take the lawn mower from the back of the shed.",
    "How great! The plants are finally starting to grow. Look at those pretty lavender flowers. Pluck one if you would like to! "
    ]

    # 2D list of connections between rooms
    map = [
        [1,11],[0,2,3],[1],[1,4,5],[3],
        [3,6,7,13],[5],[5,8,9,12],[7],[7,10],
        [9,11],[0,10],[7,13,18],[5,12,14],[13,17],
        [16],[15,17],[14,16],[12,19,20],[18],
        [18]
    ]

    # Possible navaigation choices for user
    directions = ["north", "east", "south", "west", "north east"]

    # Possible directions within each room
    # 0 - North
    # 1 - East
    # 2 - South
    # 3 - West
    # 4 - North-East
    room_directions =  [
        [0,2],[2,1,0],[3],[2,1,0],[3],
        [2,1,3,0],[3],[1,2,3,0],[0],[1,2],
        [0,2],[4,0],[2,1,0],[2,3,1],[3,0],
        [0],[2,1],[2,3],[2,0,1],[2],
        [3]
    ]

    #2D list of possible directions choices from each room
    nav = [
        ["north","south"],["south","east","north"],["west"],["south","east","north"],["west"],
        ["south","east","west","north"],["west"],["east","south","west","north"],["north"],["east","south"],
        ["north","south"],["north east","north"],["south","east","north"],["south","west","east"],["west","north"],
        ["north"],["south","east"],["south","west"],["south","north","east"],["south"],
        ["west"]

    ]

    # List of list that show which items have inventory
    items = [[],["Coat"],[],[],["Stapler"],
             [],[],[],["Cookies"],["Candle"],
             ["Car keys"],[],[],[],[],
             [],[],["Shampoo"],[],["Lawn mower"],
             ["Flowers"]
    ]

    # List of inventory (empty to start with)
    inventory = []

    # Player starts off on the Porch (room 0)
    current_roomNumber = 0
    
    # Display the map and instructions
    display_map()
    display_instructions()

    # Let the player continue playing the text adventure until they QUIT
    while True:
        # Find and print the current room name the player is in using the room number
        current_roomName = rooms[current_roomNumber]

        print(f"\nYou are at the {current_roomName}.", end = " ")
        print(room_descriptions[current_roomNumber])
        print(f"You have the following options: ")

        # Iterate through list to the possible room numbers the player can go to
        for i in range(len(map[current_roomNumber])):

            #Print the possible room numbers and names the player can go to
            possible_room_number = map[current_roomNumber][i]
            print('\t' ,rooms[possible_room_number], end = "")
            
            #Print the possible directions the player can go
            navigation = (room_directions[current_roomNumber][i])
            direct = directions [navigation]
            print(" - ", direct)

        # Ask user to input the direction or any commands ancd check if it is valid
        direction_choice = get_direction (nav, current_roomNumber, items, inventory, current_roomNumber)

        # Get the new index of the navigation and find the new room the player has moved to
        nav_index = nav[current_roomNumber].index(direction_choice)
        current_roomNumber = map[current_roomNumber][nav_index]
        

# Call main function
main()

