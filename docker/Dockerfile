FROM registry.access.redhat.com/ubi8/dotnet-70:7.0-13.20230511125012 as builder
WORKDIR /opt/app-root/src
COPY --chown=1001 . .
RUN dotnet publish -c Release


FROM registry.access.redhat.com/ubi8/dotnet-70-runtime
EXPOSE 8081
ENV ASPNETCORE_URLS=http://*:8081
COPY --from=builder /opt/app-root/src/bin /opt/app-root/src/bin
WORKDIR /opt/app-root/src/bin/Release/net7.0/publish
CMD ["dotnet", "SignalRChat.dll"]