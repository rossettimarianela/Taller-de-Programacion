# Módulo Imperativo - (Pascal)

</aside>

## Guia de Estudio:

- Algoritmos de Ordenación
    - Selección (vectores)
    - Inserción (vectores)
- Recursión
    - Listas
    - Vectores
- Árboles
    - Insertar Hijos
    - Borrar Elemento
    - Buscar en arbol
    - Calcular Max/ Min
    - Imprimir entre valores
    - Imprimir por nivel
    - Recorridos
- Extras
    - Minimos
    - Máximos

## Algoritmos de Ordenación

### Ordenación por Selección

- Funciona seleccionando el elemento más pequeño o más grande de la lista y colocándolo en su posición correcta.
- Repite este proceso hasta que la lista esté ordenada.
- Tiene una complejidad temporal de O(n^2), donde n es el número de elementos en la lista.
- Es ineficiente para listas grandes, pero simple de implementar.

```pascal
Procedure Seleccion ( var v: numeros; dimLog: integer);
var
  i, j, p, item: integer;
begin
  for i:=1 to dimLog-1 do begin {busca el mínimo v[p] entre v[i] , ..., v[N] }
    p := i;
    for j := i+1 to dimLog do
      if v[ j ] < v[ p ] then     //ordena de menor a mayor. Para ordenar de mayor a menor, invertir el signo
        p:=j;
    {intercambia v[i] y v[p] }
    item := v[ p ];
    v[ p ] := v[ i ];
    v[ i ] := item;
  end;
end;
```

### Ordenación por Inserción

- Funciona insertando cada elemento en su posición correcta dentro de la lista ordenada.
- Comienza con la segunda elemento y compara con el primero, luego con el tercero y así sucesivamente.
- Si el elemento es menor que el elemento anterior, se mueve a la posición correcta.
- Tiene una complejidad temporal de O(n^2), pero es más eficiente que la ordenación por selección para listas pequeñas o casi ordenadas.
- Es estable, es decir, mantiene el orden de elementos iguales.

```pascal
// ORDENACION DE VECTORES POR INSERCION

procedure OrdenacionPorInsercion(var v: vector; dimL: integer);
var 
	i, j, actual: integer;
begin

	for i:= 2 to dimL do begin
   		actual:=v[i];
   		j:= i-1;
   		while (j > 0) and (v[j] > actual) do begin
     			v[j+1]:=v[j];
     			j := j-1;
     		end;
		v[j+1] := actual;
	end;
end;
```

## Recursión

### Listas

```pascal
//BUSCA UN ELEMENTO EN UNA LISTA DE MANERA RECURSIVA

function buscar(l:lista; x:integer):boolean;
begin
  if(l=nil)then
    buscar:=false
  else
    if(l^.dato=x)then
      buscar:=true
    else
      buscar:=buscar(l^.sig,x);
end;
```

### Vectores

```pascal
//CALCULA LA SUMA TOTAL DE UN VECTOR DE ENTEROS DE FORMA RECURSIVA

function suma(v:vector; dimL:integer):integer;
begin
  if (dimL = 0) then
     suma := 0
  else
      suma := suma(v,dimL-1) + v[dimL]
end;
```

## Arboles

### Generar Hoja

```pascal
// INSERTAR EN UN ARBOL

procedure Insertar(m: integer; var a: arbol);
var
	aux: arbol;
begin
	if (a = nil) then begin
		new(aux);
		aux^.dato := m;
		aux^.HI := nil;
		aux^.HD := nil;
		a := aux
	end
	else
		if (m > a^.dato) then 
			Insertar (m, a^.HD)
		else
			if (m < a^.dato) then
				Insertar (m, a^.HI);
			// else, es repetido
end;
```

### Cantidad de Repetidos

```pascal
// CONTAR CANTIDAD DE VECES QUE APARECE UN ELEMENTO EN EL ARBOL 

// POR MISMO CRITERIO DE CREACION
function Cantidad_Repetidos (a:arbol; x:integer): integer;
begin
	if (a = nil) then 
		Buscar := 0
	else
		if (x = a^.dato) then
			Buscar := (Buscar(a^.HI, x) + 1)
		else
			if (x < a^.dato) then
				Buscar := Buscar(a^.HI, x)
			else
				Buscar := Buscar(a^.HD, x)
end;

// POR DIFERENTE CRITERIO
function cant_repe (a:arbol; x:integer): integer;
begin
	if (a = nil) then
		cant_repe := 0;
	else
	begin
		if (a^.dato = x) then
			cant_repe := (cant_repe(a^.HI, x) + cant_repe(a^.HD, x) + 1) // SI EL DATO ES IGUAL A X, SE SUMA 1
		else
			cant_repe := (cant_repe(a^.HI, x) + cant_repe(a^.HD, x)) // SI EL DATO ES DISTINTO A X, NO SE SUMA NADA y SE CONTINUA RECORRIENDO EL ARBOL
	end;
end;
```

### Busqueda

```pascal
// BUSCAR EN UN ARBOL RESPETANDO EL ORDEN. Devuelve un puntero de tipo arbol. Si no lo encuentra devuelve nil

function Buscar (a:arbol; x:integer): arbol;
begin
	if (a = nil) then 
		Buscar := nil
	else
		if (x = a^.dato) then
			Buscar := a
		else
			if (x < a^.dato) then
				Buscar := Buscar(a^.HI, x)
			else
				Buscar := Buscar(a^.HD, x)
end;

// BUSCAR EN UN ARBOL SIN RESPETAR EL ORDEN. Devuelve un puntero de tipo arbol. Si no lo encuentra devuelve nil

function Buscar (a:arbol; x:integer): arbol;
begin
	if (a = nil) then
		Buscar := nil
	else
		if (x = a^.dato) then
			Buscar := a
		else
                    Buscar := Buscar(a^.HI, x) or Buscar(a^.HD, x);

end;
```

### Imprimir entre valores

```pascal
procedure imprimirEntreValores(a:arbol);
begin

	if(a<>nil)then
		if(a^.dato.legajo > 2803) and (a^.dato.legajo < 6982)then begin
			write(a^.dato.nombre);
			imprimirEntreValores(a^.HI)
			imprimirEntreValores(a^.HD)
		end
		else
			if(a^.dato.legajo < 2803)then
					imprimirEntreValores(a^.HD)
			else
				if(a^.dato.legajo > 6982) then
					imprimirEntreValores(a^.HI)
end;
```

### Recorridos/ Impresión

```pascal
// RECORRIDOS TOTALES DE UN ARBOL

// EN ORDEN (Imprime de menor a mayor - Para imprimir de mayor a menor, invierto la recursion)

procedure enOrden (a:arbol);
begin
	if (a <> nil) then begin
		enOrden(a^.HI);
		write('', a^.dato);
		enOrden(a^.HD);	
	end;	
end;

// POST ORDEN may - men

procedure postOrden (a:arbol);
begin
	if (a <> nil) then begin
		postOrden(a^.HI);
		postOrden(a^.HD);
		write('', a^.dato);
	end;	
end;

// PRE ORDEN (jerarquico) Primero va por los padres y despues por todos los hijos

procedure preOrden (a:arbol);
begin
	if (a <> nil) then begin
		write('', a^.dato);
		preOrden(a^.HI);
		preOrden(a^.HD);		
	end;	
end;
```

