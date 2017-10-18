namespace _1_ZH_Farkas_Peter
{
    class Program
    {
        struct Negyzet
        {
            public int x;
            public int y;
            public int oldal;
        }

        static void Main(string[] args)
        {
            Console.Write("Adja meg hány négyzetet szeretne: ");
            int db = int.Parse(Console.ReadLine());

            Negyzet[] negyzetek = feltolt(db);

            vizsgalat(negyzetek);

            Console.ReadLine();
        }

        static Negyzet[] feltolt (int darab)
        {
            Negyzet[] tomb = new Negyzet[darab];
            Random rand = new Random();

            for(int i = 0; i < tomb.Length; i++)
            {
                tomb[i].x = rand.Next(5, 357);
                tomb[i].y = rand.Next(5, 357);
                tomb[i].oldal = rand.Next(11,34);
            }

            return tomb;
        }

        
        static void vizsgalat(Negyzet[] negyzet)
        {
            for(int i = 0; i < negyzet.Length; i++)
            {
                for(int e = 0; e < negyzet.Length; e++)
                {
                   if(e != i)
                    {
                        if (negyzet[e].x >= negyzet[i].x && negyzet[e].x <= (negyzet[i].x + negyzet[i].oldal))
                        {
                            if (negyzet[e].y <= negyzet[i].y && negyzet[e].y >= (negyzet[i].y - negyzet[i].oldal))
                            {
                                if (((negyzet[e].x - negyzet[i].x) + negyzet[e].oldal) < negyzet[i].oldal)
                                {
                                    if (((negyzet[i].y - negyzet[e].y) + negyzet[e].oldal) < negyzet[i].oldal)
                                    {
                                        Console.WriteLine("A(z) {0}. négyzet a(z) {1}. négyzeten belül van.", e, i);
                                    }
                                }

                                Console.WriteLine("A(z) {0}. és a(z) {1}. négyzet metszik egymást.", e, i);
                            }
                        }
                    }
                    
                }
            }

        }
    }
}# elso_zhmegoldas
