#Cows and Bulls
                    Console.WriteLine("What is your name: ");
                    string UserName = Console.ReadLine();
                    // generating random number
                    int[] DigitsUsed = new int[4];
                    int uniqueCount = 0; bool found;
                    Random random = new Random();
                    while (uniqueCount < 4)
                    {
                        int newDigit = random.Next(1, 10); found = false;
                        for (int i = 0; i < 4; i++)
                        {
                            if (DigitsUsed[i] == newDigit)
                            {
                                found = true; break;
                            }
                        }
                        if (!found)
                        {
                            uniqueCount++; DigitsUsed[uniqueCount - 1] = newDigit;
                        }
                    }
                    int resultNumber = 0;
                    for (int i = 0; i < 4; i++)
                    {
                        resultNumber = resultNumber * 10 + DigitsUsed[i];
                    }
                    if (resultNumber >= 1000 && resultNumber < 9999)
                    {
                    }
                    // asking the user to enter there number(validating it)
                    bool correctGuess = false;
                    int count = 0;
                    while (!correctGuess)
                    {
                        while (true)
                        {
                            Console.WriteLine("Enter a 4-digit number between 1000 and 9999 as your first guess. This number must have no repeating digits, for example 1234:"); 
                            string UserGuess = Console.ReadLine();
                            if (UserGuess.Length != 4)
                            {
                                Console.WriteLine("Invalid answer. Please enter a 4-digit number with unique digits.");
                                continue;
                            }
                            count++; bool validGuess = true;
                            for (int i = 0; i < 4; i++)
                            {
                                for (int j = i + 1; j < 4; j++)
                                {
                                    if (UserGuess[i] == UserGuess[j])
                                    {
                                        validGuess = false; break;
                                    }
                                }
                                if (!(UserGuess[i] >= '0' && UserGuess[i] <= '9'))
                                {
                                    validGuess = false; break;
                                }
                            }
                            if (validGuess && (UserGuess.CompareTo("1000") >= 0 && UserGuess.CompareTo("9999") <= 0))
                            {
                                Console.WriteLine("Valid guess!");
                            }
                            else
                            {
                                Console.WriteLine("Invalid guess. Please try again.");
                            }
                            {
                                // checks the number bulls and cows
                                int bulls = 0;
                                int cows = 0;
                                {
                                    for (int i = 0; (i < 4); i++)
                                    {
                                        if (UserGuess[i] == DigitsUsed[i] + '0')
                                        {
                                            bulls++;
                                        }
                                        else if (DigitsUsed.Contains(UserGuess[i] - '0'))
                                        {
                                            cows++;
                                        }
                                    }
                                    Console.WriteLine("Cows: " + cows + " Bulls: " + bulls);
                                    // checks if the answer is correct
                                    if (bulls == 4)
                                    {
                                        Console.WriteLine("Nice one, " + UserName + " you got it!");
                                        // outputs the amount of guesses if there answer is correct
                                        Console.WriteLine("That only required?.... " + count + " guesses!");
                                        correctGuess = true; break;
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
