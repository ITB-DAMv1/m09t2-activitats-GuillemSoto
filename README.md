## Ex1
- Process: Et dona accés a processos i et permet fer-los servir.
- ThreadState: Diu l'estat actual d'execució del thread.
- Stopwatch: Dona una serie de mètodes i propietats que pots fer servir per mesurar el temps.
- Activity: Una operació que es fa al loguejar-se.

## Ex2
string doc = "processes.txt";

Process[] processes = Process.GetProcesses();

using (StreamWriter writer = new StreamWriter(doc))
{
      foreach (Process p in processes)
      {
           Console.WriteLine("Nom: " + p.ProcessName + "PID: " + p.Id);
           writer.WriteLine("Nom: " + p.ProcessName + "PID: " + p.Id);
       }
}

## Ex3
public static void Main()
    {
        string outputFile = "firefoxThreads.txt";

        Process[] processos = Process.GetProcessesByName(firefox);

        using (StreamWriter writer = new StreamWriter(outputFile))
        {
            foreach (Process p in processos)
            {
                Console.WriteLine("Nom: " + p.ProcessName + "PID: " + p.Id);
                writer.WriteLine("Nom: " + p.ProcessName + "PID: " + p.Id);

                ShowThreads(p, writer);
            }
        }
    }

   public static void ShowThreads(Process process, StreamWriter writer)
    {
        foreach (ProcessThread thread in process.Threads)
        {
            Console.WriteLine($"ID del thread: {thread.Id}, Hora d'inici: {thread.StartTime}, Prio: {thread.PriorityLevel}");
            writer.WriteLine($"ID del thread: {thread.Id}, Hora d'inici: {thread.StartTime}, Prio: {thread.PriorityLevel}");
        }
    }

## Ex4

Start() inicia l'execució del Thread, Join() el fa esperar a que un altre Thread acabi, Sleep() el fa esperar el temps que li diguis i Kill() para el Thread.

Thread es gestiona manualment mentre que Task és automàtic, passa el mateix amb l'execució. Task es fa servir sobretot per operacions async i Thread per controlar directament els fils.

## Ex5
A)
static void Main()
    {
        for (int i = 1; i <= 5; i++)
        {
            Thread thread = new Thread(() =>
            {
                Console.WriteLine("Número" + i);
            });
            thread.Start();
        }
    }

El ordre d'execució és aleatori (encara que és majoritàriament igual perque l'isard va lent) degut a que el sistema és qui decideix on gastar recursos.

B)

static void Main()
    {
        for (int i = 5; i >= 1; i--)
        {
            Thread thread = new Thread(() =>
            {
                Thread.Sleep(i * 200); // Introduïm retard per ordenar inversament
                Console.WriteLine("Número" + i);
            });
            thread.Start();
        }
    }
