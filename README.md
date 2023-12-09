#include<iostream>
#include<vector>
using namespace std;

void instructions();
void display_misses(int misses);
void display_status(vector<char> incorrect, string answer);
void end_game(string answer, string codeword);

int main()
{
  string answer, codeword;
  int misses, i;
  char letter;

  cout<<"----------------------------\n\tH A N G M A N\n----------------------------"<<endl;
  instructions();
  cout<<"\nLET'S BEGIN!!\n"<<endl;

  cout << "Enter the codeword (word to be guessed): ";
  cin >> codeword;

  answer = string(codeword.length(), '_');

  misses=0;
  vector<char> incorrect;
  bool guess = false;

  while(answer!=codeword && misses<7)
  {
    display_misses(misses);
    display_status(incorrect, answer);

    cout<<"\n\nPlease enter your guess : ";
    cin>>letter;
    for(i=0; i<codeword.length(); i++)
      {
        if(letter==codeword[i])
        {
          answer[i]=letter;
          guess = true;
        }
      }
    if(guess)
    {
      cout<<"\nCorrect!"<<endl;
    }
    else
    {
      cout<<"Incorrect. Try Again "<<endl;
      incorrect.push_back(letter);
      misses++;
    }
    guess = false;
  }
  end_game(answer, codeword);
  return 0;
}

void instructions()
{
    cout<<"Instructions :"<<endl;
    cout<<"1. Player 2 guesses the word given by Player 1"<<endl;
    cout<<"2. Save the man from being hanged by guessing the correct letters"<<endl;
    cout<<"3. A body part is added each time you give a wrong guess."<<endl;
    cout<<"4. You get 6 guesses in total."<<endl;
}

void display_misses(int misses)
{
    if(misses==0)
    {
        cout<<"+----+"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|"<<endl;
        cout<<"|"<<endl;
        cout<<"|"<<endl;
        cout<<"========"<<endl;
    }
    else if(misses==1)
    {
        cout<<"+----+"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|  O"<<endl;
        cout<<"|"<<endl;
        cout<<"|"<<endl;
        cout<<"========"<<endl;
    }
    else if(misses==2)
    {
        cout<<"+----+"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|  O"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|"<<endl;
        cout<<"========"<<endl;
    }
    else if(misses==3)
    {
        cout<<"+----+"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|  O"<<endl;
        cout<<"| -|"<<endl;
        cout<<"|"<<endl;
        cout<<"========"<<endl;
    }
    else if(misses==4)
    {
        cout<<"+----+"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|  O"<<endl;
        cout<<"| -|-"<<endl;
        cout<<"|"<<endl;
        cout<<"========"<<endl;
    }
    else if(misses==5)
    {
        cout<<"+----+"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|  O"<<endl;
        cout<<"| -|-"<<endl;
        cout<<"| / "<<endl;
        cout<<"========"<<endl;
    }
    else if(misses==6)
    {
        cout<<"+----+"<<endl;
        cout<<"|  |"<<endl;
        cout<<"|  O"<<endl;
        cout<<"| -|-"<<endl;
        cout<<"| / /"<<endl;
        cout<<"========"<<endl;
    }
}

void display_status(vector<char> incorrect, string answer)
{
  int i;
  cout<<"Incorrect Guesses : "<<endl;
  for(i=0; i<incorrect.size(); i++)
  {
    cout<<incorrect[i]<<" ";    //prints the incorrect characters one after                                     the other in the form of an array
  }
  cout<<"\nCodeword: ";
  for(i=0; i<answer.length(); i++)
  {
    cout<<answer[i]<<" ";      //prints the correct character in the answer                                    vector at the location as that in the answer 
  }
}

void end_game(string answer, string codeword)
{
  if(answer==codeword)
  {
    cout<<"The correct word is : "<<codeword<<endl;
    cout<<"Congratulations!! You saved the person from being hanged."<<endl;
  }
  else
  {
      cout<<"Oops! Better luck next time."<<endl;
  }
}
