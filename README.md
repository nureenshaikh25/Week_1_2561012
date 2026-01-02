#include <stdio.h>
#include <conio.h>

struct product
{
    int pid;
    char name[20];
    int qty;
    float price;
    float total;
};

void main()
{
    struct product p[5];
    int i, search_id, found = 0;
    float grand_total = 0;

    clrscr();

    /* Input product details */
    for(i = 0; i < 5; i++)
    {
        printf("\nEnter details of Product %d\n", i + 1);

        printf("Product ID   : ");
        scanf("%d", &p[i].pid);

        printf("Product Name : ");
        scanf("%s", p[i].name);

        printf("Quantity     : ");
        scanf("%d", &p[i].qty);

        printf("Price        : ");
        scanf("%f", &p[i].price);

        p[i].total = p[i].qty * p[i].price;
    }

    /* Display product details */
    printf("\n\nProduct Details");
    printf("\n---------------------------------------------");
    printf("\nID\tName\tQty\tPrice\tTotal");
    printf("\n---------------------------------------------");

    for(i = 0; i < 5; i++)
    {
        printf("\n%d\t%s\t%d\t%.2f\t%.2f",
               p[i].pid, p[i].name, p[i].qty,
               p[i].price, p[i].total);

        grand_total += p[i].total;
    }

    printf("\n---------------------------------------------");
    printf("\nTotal Bill Amount = %.2f", grand_total);

    /* Search product by ID */
    printf("\n\nEnter Product ID to search: ");
    scanf("%d", &search_id);

    for(i = 0; i < 5; i++)
    {
        if(p[i].pid == search_id)
        {
            printf("\n\nProduct Found!");
            printf("\nID     : %d", p[i].pid);
            printf("\nName   : %s", p[i].name);
            printf("\nQty    : %d", p[i].qty);
            printf("\nPrice  : %.2f", p[i].price);
            printf("\nTotal  : %.2f", p[i].total);
            found = 1;
            break;
        }
    }

    if(found == 0)
    {
        printf("\n\nProduct not found!");
    }

    getch();
}
