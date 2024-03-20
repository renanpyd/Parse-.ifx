# Parse-.ifx
Análise arquivo .IFX IBM DB2


Essa semana me deparei com um problema novo. Como não usava DB2, o banco de dados da IBM, nem havia tratado dados até então para nenhum cliente que o utilizasse, não sabia que é possível exportar dados, além do famoso .csv, em formato .ifx.

O desafio era subir e tratar esses dados em um data lake com Pyspark. Porém não encontrei na documentação do Spark nada relacionado a esse formato. 

Então fui atrás de documentação, fóruns e blogs sobre o IBM DB2, e eis que encontrei algumas informações valiosas, que me guiaram para iniciar esse estudo e realizar alguns testes para estudo de caso.

No nosso querido Stackoverflow (https://stackoverflow.com/questions/8570930/converting-ibm-db2-ixf-file-to-csv-or-xml) encontrei as seguintes informações:
    O formato PC/IXF é bastante complexo e praticamente desconhecido por programas fora do DB2. Escrever seu próprio analisador PC/IXF apenas para converter um arquivo IXF diretamente para algum outro formato pode demorar um pouco. Uma alternativa mais rápida é emitir um comando IMPORT no servidor DB2 e especificar CREATE INTO em vez de INSERT INTO, o que gerará uma tabela totalmente nova que pode acomodar o conteúdo do arquivo que está sendo importado. Isso permitirá que você execute um comando EXPORT na nova tabela para despejar as linhas em um formato delimitado.

MAS... E quando você não tem acesso ao banco? E quando você recebew os dados nesse formato e precisa tratalo em outro sistema fora do nativo/legado?

Segue um notebook Python documentado com o processo para o tratamento desse tipo de caso.
