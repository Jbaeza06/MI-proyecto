# Modelo de datos (Room)

La app usará **Room** como capa de persistencia local (requisito del curso).

## Entidad

### `ExpenseEntity`
| Campo         | Tipo             | Notas                                       |
|---------------|------------------|---------------------------------------------|
| `id`          | `String`         | `@PrimaryKey` (UUID)                        |
| `title`       | `String`         | Descripción del gasto                       |
| `amountCents` | `Long`           | Monto en **centavos** (evita errores Float) |
| `dateEpoch`   | `Long`           | Fecha en milisegundos desde epoch           |

> Guardar dinero como enteros (`amountCents`) es una práctica recomendada para evitar redondeos.

## DAO (Data Access Object)

```kotlin
@Dao
interface ExpenseDao {
    @Query("SELECT * FROM expenses ORDER BY dateEpoch DESC")
    fun getAll(): Flow<List<ExpenseEntity>>

    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun upsert(expense: ExpenseEntity)

    @Delete
    suspend fun delete(expense: ExpenseEntity)
}
```

## Base de datos

```kotlin
@Database(entities = [ExpenseEntity::class], version = 1, exportSchema = true)
abstract class AppDatabase : RoomDatabase() {
    abstract fun expenseDao(): ExpenseDao
}
```

## Dominio ⇄ Base de datos
- **Dominio**: `Expense(id: String, title: String, amountCents: Long, dateEpoch: Long)`
- **DB**: `ExpenseEntity` con los mismos campos (mapeo 1:1).

## Migraciones
- Versión inicial **1**. Las migraciones se agregarán cuando cambie el esquema.

## Justificación (según arquitectura vista en clase)
- Room implementa una capa de persistencia limpia dentro del patrón **Repository**.
- Exponer datos con `Flow` permite UI reactiva con Jetpack.
