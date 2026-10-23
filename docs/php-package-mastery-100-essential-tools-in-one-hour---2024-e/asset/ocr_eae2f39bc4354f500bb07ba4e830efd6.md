# 69. Symfony Console

The Symfony Console component allows developers to create command-line commands. This can be used to automate tasks, such as running migrations, clearing caches, or other application-specific commands.

Ex:Symfony Console

```
// Example of creating a console command in Symfony Console
use Symfony\Component\Console\Command\Command;
use Symfony\Component\Console\Input\InputInterface;
use Symfony\Component\Console\Output\OutputInterface;
class GreetCommand extends Command
{
protected static $defaultName = 'app:greet';
protected function configure(): void
{
$this
->setDescription('Greets a user.')
->setHelp('This command allows you to greet a user...');
}
protected function execute(InputInterface $input, OutputInterface $output): int
{
$output->writeln('Hello, Symfony Console User!');
return Command::SUCCESS;
}
}
```