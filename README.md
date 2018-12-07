using System;
using System.Collections.Generic;
using System.Text;
using System.Linq;

namespace AI
{
    class LarsPatrikBengtsson : Player //Denna spelare fungerar exakt som MyPlayer. Ändra gärna i denna för att göra tester.
    {

        public LarsPatrikBengtsson() //Skriv samma namn här
        {
            Name = "LarsPatrikBengtsson"; //Skriv in samma namn här
        }

        public override bool Knacka(int round) //Returnerar true om spelaren skall knacka, annars false
        {
            if (Game.Score(this) >= 20 && round <= 4)
            {
                return true;
            }
            else if (Game.Score(this) >= 22)
            {
                return true;
            }
            else
            {
                return false;
            }
        }

        public override bool TaUppKort(Card card) // Returnerar true om spelaren skall ta upp korten på skräphögen (card), annars false för att dra kort från leken.
        {
            if (card.Value == 11 || (card.Value > 7 && card.Suit == BestSuit))
            {
                return true;
            }
            if(card.Value < card.)
            {

            }
            else
            {
                return false;
            }

        }

        public override Card KastaKort()  // Returnerar det kort som skall kastas av de fyra som finns på handen
        {
            Game.Score(this);
            Card worstCard = Hand.First();
            for (int i = 1; i < Hand.Count; i++)
            {
                if (CardValue(Hand[i]) < CardValue(worstCard))
                {
                    worstCard = Hand[i];
                }

            }
            return worstCard;

        }

        public override void SpelSlut(bool wonTheGame) // Anropas när ett spel tar slut. Wongames++ får ej ändras!
        {
            if (wonTheGame)
            {
                Wongames++;
            }

        }

        private int CardValue(Card card) // Hjälpmetod som kan användas för att värdera hur bra ett kort är
        {
            if (card.Suit == BestSuit)
            {
                return card.Value + 100000;
            }
            return card.Value;
        }
    }
}
