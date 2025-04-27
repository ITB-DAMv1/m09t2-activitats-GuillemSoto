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
