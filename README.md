# PROJEK-ALPRO-KEL-12-2025







#include <stdio.h>
#include <string.h>
#define MAX_RESERVATIONS 100

typedef struct {
    char name[50];
    int Customer;
    int nomor_antrian;
    int ordered_food;  
} Reservation;

Reservation reservations[MAX_RESERVATIONS];
int reservation_count = 0;
int next_antrian_number = 1;

void addReservation(char name[], int people, int food_order);
void viewReservations();

int main() {
    int choice;
    char name[50];
    int Customer;
    int Pesan;
    
    do {
        printf("\n<<<-----Antrian Makanan Cepat Saji----->>>\n");
        printf("\n1. Antrian Customer\n");
        printf("2. Menu\n");
        printf("3. Pesanan Selesai\n");
        printf("\nSilahkan dipilih: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("\nNama Customer: ");
                scanf("%s", name);
                printf("Nomor antrian: ");
                scanf("%d", &Customer);
                printf("\nPilih Makanan:\n");
                printf("1. Mie Ayam\n");
                printf("2. Mie Yamin\n");
                printf("3. Mie Baso\n");
                printf("4. Baso Urat\n");
                printf("Pesan Apa: ");
                scanf("%d", &Pesan);
                addReservation(name, Customer, Pesan);
                break;
            case 2:
                printf("Menu Makanan:\n");
                printf("1. Mie Ayam\n");
                printf("2. Mie Yamin\n");
                printf("3. Mie Baso\n");
                printf("4. Baso Urat\n");
                break;
            case 3:
                viewReservations();
                break;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 3);

    return 0;
}

void addReservation(char name[], int people, int food_order) {
    if (reservation_count < MAX_RESERVATIONS) {
        strcpy(reservations[reservation_count].name, name);
        reservations[reservation_count].Customer = people;
        reservations[reservation_count].nomor_antrian = next_antrian_number++;
        reservations[reservation_count].ordered_food = food_order;  
        reservation_count++;
        printf("\nPelanggan berhasil ditambahkan ke antrean!\n");
    } else {
        printf("Tidak dapat menambahkan pelanggan. Antriannya penuh.\n");
    }
}

void viewReservations() {
    if (reservation_count == 0) {
        printf("No customers in the queue.\n");
    } else {
        printf("\nAntrian saat ini:\n");
        for (int i = 0; i < reservation_count; i++) {
            printf("%d. Name: %s\nCustomer: %d\nAntrian: %d\n", 
                   i + 1, reservations[i].name, reservations[i].Customer, reservations[i].nomor_antrian);
            printf("Makanan Yang di Pesan: ");
            switch (reservations[i].ordered_food) {
                case 1:
                    printf("Mie Ayam\n");
                    break;
                case 2:
                    printf("Mie Yamin\n");
                    break;
                case 3:
                    printf("Mie Baso\n");
                    break;
                case 4:
                    printf("Baso Urat\n");
                default:
                    printf("\nMakanan Berhasil Dipesan\n");
            }
            printf("\n");
        }
    }
}
