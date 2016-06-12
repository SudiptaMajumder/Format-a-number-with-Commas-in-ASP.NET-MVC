# Format-a-number-with-Commas-in-ASP.NET-MVC

In the view page (.chtml) I have used this :

if (item.AMOUNT < 0)//Determine negative number
{
        item.CREDITAMT = item.CREDITAMT * (-1);// make that positive
        ccheck = 1;// Flag for negative check
        string convert = Convert.ToString(item.AMOUNT);
        creditamt = CommainAmount.AmountwithComma(convert);// This link up with DataAccess Folder
}
else
 {
        ccheck = 0;//flag for positive check
        string convert = Convert.ToString(item.AMOUNT);
        creditamt = CommainAmount.AmountwithComma(convert);// This link up with DataAccess Folder
 }
 
 
 =============================================================================================
 In the CLASS Folder there are ComminAmount Class and this class hold inner method like this 'AmountwithComma method':
 (CommainAmount.cs)
   public static string AmountwithComma(string CVal)
  {

            string value = "", gotpoint = "", commainvalue = "", firstpart = "", secondpart = "", thirdpart = "", fourthpart = "", finalvalue = "";
            int lengthdebit = CVal.Length;
          

          
          
            for (int i = 0; i < lengthdebit; i++)
            {
                if (CVal[i] == '.')
                {
                    value = CVal.Substring(0, i);
                    commainvalue = CVal.Substring(i, (lengthdebit - i));
                    gotpoint = "y";
                    break;
                }
            }
            if (gotpoint == "y")
            {
                int valuelength = value.Length;
                if (valuelength > 3 && valuelength > 5 && valuelength > 7)
                {
                    value = new string(value.ToCharArray().Reverse().ToArray());
                    firstpart = value.Substring(0, 3);
                    secondpart = value.Substring(3, 2);
                    thirdpart = value.Substring(5, 2);
                    fourthpart = value.Substring(7, valuelength - 7);
                    finalvalue = firstpart + "," + secondpart + "," + thirdpart + "," + fourthpart;
                    finalvalue = new string(finalvalue.ToCharArray().Reverse().ToArray());
                    finalvalue = finalvalue + commainvalue;
                }
                else if (valuelength > 3 && valuelength > 5)
                {
                    value = new string(value.ToCharArray().Reverse().ToArray());
                    firstpart = value.Substring(0, 3);
                    secondpart = value.Substring(3, 2);

                    thirdpart = value.Substring(5, valuelength - 5);
                    finalvalue = firstpart + "," + secondpart + "," + thirdpart;
                    finalvalue = new string(finalvalue.ToCharArray().Reverse().ToArray());
                    finalvalue = finalvalue + commainvalue;
                }
                else if (valuelength > 3)
                {
                    value = new string(value.ToCharArray().Reverse().ToArray());
                    firstpart = value.Substring(0, 3);


                    secondpart = value.Substring(3, valuelength - 3);
                    finalvalue = firstpart + "," + secondpart;
                    finalvalue = new string(finalvalue.ToCharArray().Reverse().ToArray());
                    finalvalue = finalvalue + commainvalue;
                }
                else
                {
                    finalvalue = value;
                    finalvalue = finalvalue + commainvalue;
                }
            }
            else
            {
                finalvalue = CVal;
            }


            return finalvalue;

        }
  }


That's it. Enjoy your code. Thank you.
