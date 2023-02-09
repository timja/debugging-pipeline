def secrets = [
        [secretType: 'Secret', name: 'OWASPPostgresDb-v6-Account', version: '', envVariable: 'OWASPDB_V6_ACCOUNT'],
        [secretType: 'Secret', name: 'OWASPPostgresDb-v6-Password', version: '', envVariable: 'OWASPDB_V6_PASSWORD']
]

node {
    azureKeyVault(secrets) {
        steps.sh(
                './gradlew --no-daemon --init-script init.gradle --stacktrace -DdependencyCheck.failBuild=true -Dcve.check.validforhours=24 -Danalyzer.central.enabled=false -Ddata.driver_name="org.postgresql.Driver" -Ddata.connection_string="jdbc:postgresql://owaspdependency-v6-prod.postgres.database.azure.com/owaspdependencycheck" -Ddata.user=$OWASPDB_V6_ACCOUNT -Ddata.password=$OWASPDB_V6_PASSWORD -Danalyzer.retirejs.enabled=false -Danalyzer.ossindex.enabled=false dependencyCheckAggregate'
        )
    }
}
