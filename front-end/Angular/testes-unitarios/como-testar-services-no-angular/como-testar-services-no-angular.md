# Como testar services no angular?

Existem diversas maneiras, aqui vai algumas:

## Utilizando .and.returnValue(of()) com .subscribe e done()

Exemplo:

```
describe('getCommentHistory', () => {

  // Aqui eu verifico se o serviço está chamando como deveria ser chamado.
  it('should call a service with these params', () => {
    const spy = spyOn<any>(service['http'], 'get');
    let params = new HttpParams();
    const queryParams = { order_by_asc: false, order_by_property: 'id', page_index: 1, page_size: 8 };
    Object.entries(queryParams).forEach(([key,value]) => params = params.set(key,value));
    service.getCommentHistory(1, queryParams);
    expect(spy).toHaveBeenCalledWith(`minha_url_expto/1`, { params });
  });

  /*
    Aqui eu estou garantindo que o dado retornado vai ser o mesmo do enviado,
    um .pipe(map()) pode transformar os dados retornados por exemplo, e quebrar outras
    dependencias que utilizavam o retorno antigo.
  */
  it('should not change the data when make a request', (done) => {
    const objeto_esperado_no_retorno = { nome: 'xpto' };
    const queryParams = { order_by_asc: false, order_by_property: 'id', page_index: 1, page_size: 8 };
    spyOn(service['http'], 'get').and.returnValue(of(JSON.parse(JSON.stringify(objeto_esperado_no_retorno))));
    service.getCommentHistory(1,queryParams)
      .subscribe(data => {
        done();
        expect(data).toEqual(objeto_esperado_no_retorno);
      });
  });

});
```
