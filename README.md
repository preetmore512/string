# string

#include <iostream>
#include <string>
using namespace std;

class String
{
    string str;

public:
    void accept()
    {
        cout << "Enter a string: ";
        getline(cin, str);
    }

    void frequency()
    {
        char ch;
        int count = 0;

        cout << "Enter character to find: ";
        cin >> ch;

        for (int i = 0; i < str.length(); i++)
        {
            if (str[i] == ch)
                count++;
        }

        cout << "Frequency = " << count << endl;
    }

    void extract()
    {
        int pos, len;

        cout << "Enter starting position (0-based): ";
        cin >> pos;

        cout << "Enter length: ";
        cin >> len;

        if (pos >= 0 && pos < str.length() && len >= 0)
            cout << "Extracted string = "
                 << str.substr(pos, len) << endl;
        else
            cout << "Invalid position or length!" << endl;
    }

    void removeChar()
    {
        char ch;
        string result = "";

        cout << "Enter character to remove: ";
        cin >> ch;

        for (int i = 0; i < str.length(); i++)
        {
            if (str[i] != ch)
                result += str[i];
        }

        cout << "String after removal = "
             << result << endl;
    }

    void replaceString()
    {
        string x, w;

        cout << "Enter substring to replace (x): ";
        cin >> x;

        cout << "Enter new string (w): ";
        cin >> w;

        if (x.empty())
        {
            cout << "Substring cannot be empty!" << endl;
            return;
        }

        size_t pos = 0;

        while ((pos = str.find(x, pos)) != string::npos)
        {
            str.replace(pos, x.length(), w);
            pos += w.length();
        }

        cout << "String after replacement = "
             << str << endl;
    }

    void palindrome()
    {
        string rev = "";

        for (int i = str.length() - 1; i >= 0; i--)
        {
            rev += str[i];
        }

        if (str == rev)
            cout << "String is a palindrome." << endl;
        else
            cout << "String is not a palindrome." << endl;
    }
};

int main()
{
    String s;
    int choice;

    s.accept();

    do
    {
        cout << "\n----- STRING OPERATIONS -----" << endl;
        cout << "1. Frequency of a character" << endl;
        cout << "2. Extract a substring" << endl;
        cout << "3. Remove a character" << endl;
        cout << "4. Replace a substring" << endl;
        cout << "5. Check palindrome" << endl;
        cout << "6. Exit" << endl;

        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice)
        {
            case 1:
                s.frequency();
                break;

            case 2:
                s.extract();
                break;

            case 3:
                s.removeChar();
                break;

            case 4:
                s.replaceString();
                break;

            case 5:
                s.palindrome();
                break;

            case 6:
                cout << "Exiting program..." << endl;
                break;

            default:
                cout << "Invalid choice!" << endl;
        }

    } while (choice != 6);

    return 0;
}
