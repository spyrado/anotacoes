# O nome não é DECORATORS mas vou considerar como se fosse.

`[HttpGet]` -> Voce permite que o metodo seja um endpoint do tipo `Get` ( juntamente com [ApiController] )<br>
`[HttpPost]` -> Voce permite que o metodo seja um endpoint do tipo `Post` ( juntamente com [ApiController] ) <br>
`[HttpPut]` -> Voce permite que o metodo seja um endpoint do tipo `Put` ( juntamente com [ApiController] )<br>
`[HttpPatch]` -> Voce permite que o metodo seja um endpoint do tipo `Patch` ( juntamente com [ApiController] )<br>
`[HttpDelete]` -> Voce permite que o metodo seja um endpoint do tipo `Delete` ( juntamente com [ApiController] ) <br>
`[JsonIgnore]` -> Sempre vai ignorar a propriedade ao enviar para o front. <br>
`[JsonIgnore(Condition = JsonIgnoreCondition.Never)]` -> Sempre vai Serializar e Desserializar a propriedade <br>
`[JsonIgnore(Condition = JsonIgnoreCondition.WhenWritingDefault)]` -> A propriedade só será ignorada se for null <br>