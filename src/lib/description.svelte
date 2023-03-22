<script lang="ts">
    
</script>
<article>
    <div>
        <span>
            <h1>
                <img src="./subir.jpg" height={34} width={34}>
            <img/>
                1.Subir
         </h1>
        
         <p>
            Para obtener los mejores resultados, el sujeto u objeto del que desea quitar su fondo debe tener bordes definidos.
         </p>
        </span>
        <br/>
        <div>
            <span>
                <h1>
                    <img src="./eliminar2.jpg" height={34} width={34}/>
                    2.Eliminar
                </h1>
                <p>
                    Cuando subes tu imagen, la inteligencia artificial de cloudinary elimina automaticamente el fondo 
                </p>
            </span>
        </div>
        <br/>
        <div>
            <span>
                <h1>
                    <img src="./icono descarga.jpg" height={34} width={34}/>
                    3.Descargar

                </h1>
                <p>
                    Descarga tu nueva imagen con fondo transparente
                </p>
            </span>
        </div>
    </div>
</article>

<style>
article{
    display: columns;
    flex-wrap: wrap;
    gap: 2.4rem;
    justify-content: center;
}
span{
    display:grid;
    grid-template-columns: auto 1fr;
    background:#113b70;
    padding: 3.4rem;
    gap: 1.2rem;
    border-radius: 1.2rem;
    max-width: 30rem;
    color: aliceblue;
}
</style>
