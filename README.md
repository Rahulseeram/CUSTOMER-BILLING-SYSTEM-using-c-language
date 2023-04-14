# CUSTOMER-BILLING-SYSTEM-using-c-language
#it is regarding customer billing system using c language
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_ITEMS 50

struct Item {
    char name[20];
    int quantity;
    float price;
};
struct Item items[MAX_ITEMS];
int item_count = 0;

void show_menu() {
	printf("MENU   : \n");
	printf("--------\n");
	printf("s.no                  itemname                    price \n");
	printf("-----------------------------------------------------------\n");
	printf("1.                    Hamburger                    186.65 \n");
	printf("2.                    Cheeseburger                 140.00 \n");
	printf("3.                    Hotdog                       139.79 \n");
	printf("4.                    French Fries                 180.05 \n");
	printf("5.                    Soda                         20.00  \n");
	printf("6.                    Water                        20.00  \n");
	printf("7.                    Chicken fry                  400.23 \n");
	printf("8.                    Tandoori                     250.03 \n");
	printf("9.                    Biriyani                     200.00 \n");
	printf("\n");
	printf("****************************************************************************************************************\n");
    printf("Welcome to the customer billing system.\n\n");
    printf("1. Add new item\n");
    printf("2. Delete item\n");
    printf("3. Billing\n");
    printf("4. Payment\n");
    printf("0. Exit\n\n");
    
}

void add_item() {
    if (item_count == MAX_ITEMS) {
        printf("Maximum number of items reached.\n");
        return;
    }

    struct Item item;
    printf("Enter item name: ");
    scanf("%s", item.name);
    printf("Enter item quantity: ");
    scanf("%d", &item.quantity);
    printf("Enter item price: ");
    scanf("%f", &item.price);

    items[item_count] = item;
    item_count++;

    printf("Item added successfully.\n");
}

void delete_item() {
    if (item_count == 0) {
        printf("No items found.\n");
        return;
    }

    int index;
    printf("Enter item index to delete (1-%d): ", item_count);
    scanf("%d", &index);

    if (index < 1 || index > item_count) {
        printf("Invalid item index.\n");
        return;
    }

    for (int i = index - 1; i < item_count - 1; i++) {
        items[i] = items[i + 1];
    }

    item_count--;

    printf("Item deleted successfully.\n");
}

void billing() {
    if (item_count == 0) {
        printf("No items found.\n");
        return;
    }

    float total_price = 0;
    printf("Bill:\n\n");
    printf("Item name\tQuantity\tPrice\n");

    for (int i = 0; i < item_count; i++) {
        printf("%s\t\t%d\t\t%.2f\n", items[i].name, items[i].quantity, items[i].price);
        total_price += items[i].quantity * items[i].price;
    }

    printf("\nTotal price: %.2f\n", total_price);
}

void payment() {
    printf("Payment completed successfully.\n");
}

int main() {
    int choice;
    

    do {
        show_menu();
        printf("Enter choice (0-4): ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                add_item();
                break;
            case 2:
                delete_item();
                break;
            case 3:
            	printf("****---------------------------------------------------------------------------------------------------------------**** \n");
                billing();
                printf("****---------------------------------------------------------------------------------------------------------------**** \n");
                break;
            case 4:
                payment();
                break;
            case 0:
                printf("Exiting.\n");
                break;
            default:
                printf("Invalid choice.\n");
                break;
        }

        printf("\n");

    } while (choice != 0);

    return 0;
}
