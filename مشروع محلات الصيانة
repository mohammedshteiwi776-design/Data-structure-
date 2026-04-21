#include <iostream>
#include <string>
using namespace std;

struct Device
{
    int id;
    string customer;
    string type;
    string problem;
    string status;

    Device *next;
    Device *prev;

    Device(int i, string c, string t, string p)
    {
        id = i;
        customer = c;
        type = t;
        problem = p;
        status = "UnderRepair";
        next = prev = NULL;
    }
};

class Maintenance
{
private:
    Device *head;

public:
    Maintenance()
    {
        head = NULL;
    }

    // add first
    void addFirst(int id, string c, string t, string p)
    {
        Device *newNode = new Device(id, c, t, p);

        if (head == NULL)
        {
            newNode->next = newNode->prev = newNode;
            head = newNode;
        }
        else
        {
            Device *last = head->prev;

            newNode->next = head;
            newNode->prev = last;

            last->next = newNode;
            head->prev = newNode;

            head = newNode;
        }

        cout << "Device added at beginning\n";
    }

    // add last
    void addLast(int id, string c, string t, string p)
    {
        Device *newNode = new Device(id, c, t, p);

        if (head == NULL)
        {
            newNode->next = newNode->prev = newNode;
            head = newNode;
        }
        else
        {
            Device *last = head->prev;

            newNode->next = head;
            newNode->prev = last;

            last->next = newNode;
            head->prev = newNode;
        }

        cout << "Device added at end\n";
    }

    // add at position
    void addAtPosition(int id, string c, string t, string p, int pos)
    {
        if (head == NULL || pos <= 1)
        {
            addFirst(id, c, t, p);
            return;
        }

        Device *current = head;

        for (int i = 1; i < pos - 1; i++)
        {
            current = current->next;

            if (current == head)
            {
                cout << "Position not valid\n";
                return;
            }
        }

        Device *newNode = new Device(id, c, t, p);

        newNode->next = current->next;
        newNode->prev = current;

        current->next->prev = newNode;
        current->next = newNode;

        cout << "Device added at position\n";
    }

    // delete first
    void deleteFirst()
    {
        if (head == NULL)
        {
            cout << "System empty\n";
            return;
        }

        if (head->next == head)
        {
            delete head;
            head = NULL;
        }
        else
        {
            Device *temp = head;
            Device *last = head->prev;

            head = head->next;
            last->next = head;
            head->prev = last;

            delete temp;
        }

        cout << "First device deleted\n";
    }

    // delete last
    void deleteLast()
    {
        if (head == NULL)
        {
            cout << "System empty\n";
            return;
        }

        if (head->next == head)
        {
            delete head;
            head = NULL;
        }
        else
        {
            Device *last = head->prev;

            last->prev->next = head;
            head->prev = last->prev;

            delete last;
        }

        cout << "Last device deleted\n";
    }

    // delete by id
    void deleteById(int id)
    {
        if (head == NULL)
        {
            cout << "System empty\n";
            return;
        }

        Device *current = head;

        do
        {
            if (current->id == id)
            {
                if (current->next == head && current->prev == head)
                {
                    delete current;
                    head = NULL;
                }
                else
                {
                    current->prev->next = current->next;
                    current->next->prev = current->prev;

                    if (current == head)
                        head = current->next;

                    delete current;
                }

                cout << "Device deleted\n";
                return;
            }

            current = current->next;

        } while (current != head);

        cout << "ID not found\n";
    }

    // update status
    void markFixed(int id)
    {
        if (head == NULL)
        {
            cout << "System empty\n";
            return;
        }

        Device *current = head;

        do
        {
            if (current->id == id)
            {
                current->status = "Fixed";
                cout << "Device updated to Fixed\n";
                return;
            }

            current = current->next;

        } while (current != head);

        cout << "ID not found\n";
    }

    // show forward
    void showForward()
    {
        if (head == NULL)
        {
            cout << "System empty\n";
            return;
        }

        Device *current = head;

        do
        {
            cout << current->id << " | "
                 << current->customer << " | "
                 << current->type << " | "
                 << current->problem << " | "
                 << current->status << endl;

            current = current->next;

        } while (current != head);
    }

    // show reverse
    void showReverse()
    {
        if (head == NULL)
        {
            cout << "System empty\n";
            return;
        }

        Device *current = head->prev;
        Device *last = head->prev;

        do
        {
            cout << current->id << " | "
                 << current->customer << " | "
                 << current->type << " | "
                 << current->problem << " | "
                 << current->status << endl;

            current = current->prev;

        } while (current != last);
    }
};

int main()
{
    Maintenance system;
    int choice, id, pos;
    string customer, type, problem;

    do
    {
        cout << "\n1 Add\n2 Delete\n3 Fix\n4 Show\n5 Exit\n";
        cin >> choice;

        switch (choice)
        {
        case 1:
        {
            int opt;
            cout << "1 First  2 Last  3 Position\n";
            cin >> opt;

            cout << "ID: ";
            cin >> id;
            cout << "Customer: ";
            cin >> customer;
            cout << "Device type: ";
            cin >> type;
            cout << "Problem: ";
            cin >> problem;

            if (opt == 1)
                system.addFirst(id, customer, type, problem);
            else if (opt == 2)
                system.addLast(id, customer, type, problem);
            else
            {
                cout << "Position: ";
                cin >> pos;
                system.addAtPosition(id, customer, type, problem, pos);
            }

            break;
        }

        case 2:
        {
            int opt;
            cout << "1 First  2 Last  3 By ID\n";
            cin >> opt;

            if (opt == 1)
                system.deleteFirst();
            else if (opt == 2)
                system.deleteLast();
            else
            {
                cout << "ID: ";
                cin >> id;
                system.deleteById(id);
            }

            break;
        }

        case 3:
            cout << "ID: ";
            cin >> id;
            system.markFixed(id);
            break;

        case 4:
        {
            int opt;
            cout << "1 Forward  2 Reverse\n";
            cin >> opt;

            if (opt == 1)
                system.showForward();
            else
                system.showReverse();

            break;
        }

        case 5:
            cout << "Exit...\n";
            break;

        default:
            cout << "Wrong choice\n";
        }

    } while (choice != 5);

    return 0;
}
