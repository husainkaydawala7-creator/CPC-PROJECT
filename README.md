#CPC PROJECT
#include <stdio.h>                                                      
#include <stdlib.h>

#define MAX_SEATS 30

// Structure to represent a bus
struct Bus{
    int seats[MAX_SEATS];
};

// Initialize the bus with all seats available
void initializeBus(struct Bus*bus){
    for(int i=0;i<MAX_SEATS;++i){
        bus->seats[i]=0; // 0 represents an available seat

    }
}

// Display the available seats in the bus
void displaySeats(struct Bus bus){
    printf("Available Seats: ");
    for(int i=0;i<MAX_SEATS;++i){
        if(bus.seats[i]==0) {
            printf("%d ",i+1);
        }
    }
    printf("\n");
}

// Book a ticket
void bookTicket(struct Bus*bus,int seatNumber){
    if(seatNumber<1||seatNumber>MAX_SEATS){
        printf("Invalid seat number. Please choose a seat between 1 and %d.\n",MAX_SEATS);
        return;
    }

    if (bus->seats[seatNumber-1]==0){
        bus->seats[seatNumber-1]=1; // 1 represents a booked seat
        printf("Ticket booked successfully for seat %d.\n",seatNumber);
    }
    else{
        printf("Seat %d is already booked. Please choose another seat.\n",seatNumber);
    }
}

// Cancel a booked ticket
void cancelTicket(struct Bus*bus,int seatNumber){
    if(seatNumber<1||seatNumber>MAX_SEATS){
        printf("Invalid seat number. Please choose a seat between 1 and %d.\n",MAX_SEATS);
        return;
    }

    if(bus->seats[seatNumber-1]==1){
        bus->seats[seatNumber-1]=0; // 0 represents an available seat
        printf("Ticket canceled successfully for seat %d.\n",seatNumber);
    }else{
        printf("Seat %d is not booked. Nothing to cancel.\n",seatNumber);
    }
}

int main(){
    struct Bus bus;
    initializeBus(&bus);
    int choice,seatNumber;
    do{
        printf("\nBus Ticket Reservation System\n");
        printf("1. Display available seats\n");
        printf("2. Book a ticket\n");
        printf("3. Cancel a ticket\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d",&choice);

        switch (choice){
            case 1:
                displaySeats(bus);
                break;
            case 2:
                printf("Enter the seat number you want to book: ");
                scanf("%d",&seatNumber);
                bookTicket(&bus,seatNumber);
                break;
            case 3:
                printf("Enter the seat number you want to cancel: ");
                scanf("%d",&seatNumber);
                cancelTicket(&bus,seatNumber);
                break;
            case 4:
                printf("Exiting the program. Goodbye!\n");
                break;
            default:
                printf("Invalid choice. Please enter a valid option.\n");
        }
    } while (choice!=4);
    return 0;
}

DESCRIPTION:-

This program is a simple Bus Ticket Reservation System written in the C programming language. It uses a structure to represent a bus that contains an array of 30 seats. Each seat is stored as an integer: 0 for an available seat and 1 for a booked seat. When the program starts, all seats are initialized to 0, meaning they are empty and ready for booking.

The system provides a menu-driven interface that allows the user to perform four main actions:

1. Display available seats – The program loops through all seats and prints the numbers of seats that are still free.


2. Book a ticket – The user enters a seat number, and the system checks if it is valid and available. If so, it marks the seat as booked.


3. Cancel a ticket – The user can cancel a previously booked seat, and the system will mark it as available again.


4. Exit the program – Ends the loop and closes the application.



Input validation is included to prevent invalid seat numbers or duplicate bookings. The system continues running in a loop until the user chooses to exit. This program demonstrates fundamental C programming concepts such as arrays, structures, pointer usage, functions, loops, and conditional statements, making it a helpful learning project for beginners.
